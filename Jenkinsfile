
pipeline {
    agent { label 'sapo' }

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-demo-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                  docker stop demo-container || true
                  docker rm demo-container || true
                  docker run -d -p 5000:5000 --name demo-container jenkins-demo-app
                '''
            }
        }
    }
}
