pipeline {

    agent any

    stages {

        stage('Show Configuration') {
            steps {
                echo 'Deployment configuration:'
                sh 'ls -la'
                sh 'cat docker-compose.yml'
            }
        }

        stage('Pull Image') {
            steps {
                echo 'Pulling latest Docker image'
                sh 'docker compose pull'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application'
                sh 'docker compose up -d'
            }
        }

        stage('Verify') {
            steps {
                echo 'Checking deployment status'
                sh 'docker compose ps'
                sh 'docker ps'
            }
        }
    }

    post {
        success {
            echo 'Deployment completed successfully!'
        }

        failure {
            echo 'Deployment failed!'
        }
    }
}