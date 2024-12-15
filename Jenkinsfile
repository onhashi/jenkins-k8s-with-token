pipeline {
  environment {
    dockerimagename = "santanarulez/react-app"
    dockerImage = ""
  }
  agent any
  stages {
    stage('Checkout Source') {
      steps {
        git 'https://github.com/onhashi/jenkins-kubernetes-deployment.git'
      }
    }
    stage('Login to Kubernetes') {
      steps {
        script {

          withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'local-kind-with-token', contextName: 'kind-kind', credentialsId: 'CUSTOM-TOKEN', namespace: 'default', serverUrl: 'https://kind-control-plane:6443/']]) }
            sh 'kubectl get pods'
            sh 'kubectl get nodes'
          }
          
        }
      }
    }
  }
}
