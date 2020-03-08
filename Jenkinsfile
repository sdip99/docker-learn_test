pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                sh 'mvn -f pom.xml clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('Docker image build'){
            steps{
                sh 'docker build . -t tomcatsampwebapp:${env.BUILD_ID}'

            }
            
        }
    }
}