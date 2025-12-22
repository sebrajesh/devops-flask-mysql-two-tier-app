pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                git branch: 'main', url: 'https://github.com/sebrajesh/devops-two-tier-flask-app-RS.git'
            }
        }
        stage('Build image') {
            steps {
                sh 'docker build -t flask-app .'
            }
        }
        stage('Deploy with docker compose') {
            steps {
                // remove existing containers if any
                sh 'docker compose down || true'
                // start app, rebuilding images if necessary
                sh 'docker compose up -d --build'
            }
        }
    }
}