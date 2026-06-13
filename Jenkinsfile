pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/vivinmathew26-byte/CI-CD-.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t smart-tracker:latest .'
            }
        }
        stage('Load Image to Minikube') {
            steps {
                sh 'minikube image load smart-tracker:latest'
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f deployment.yml'
                sh 'kubectl rollout restart deployment smart-tracker-deployment'
            }
        }
        stage('Verify') {
            steps {
                sh 'kubectl get pods'
            }
        }
    }
}
