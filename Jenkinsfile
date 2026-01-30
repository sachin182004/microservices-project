pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/sachin182004/microservices-project.git'
      }
    }

    stage('Build Images') {
      steps {
        sh 'docker build -t sachindksachin/user-service user-service/'
        sh 'docker build -t sachindksachin/product-service product-service/'
      }
    }

    stage('Push Images') {
      steps {
        sh 'docker push sachindksachin/user-service'
        sh 'docker push sachindksachin/product-service'
      }
    }

    stage('Deploy to Kubernetes') {
      steps {
        sh 'kubectl apply -f k8s/'
      }
    }
  }
}

