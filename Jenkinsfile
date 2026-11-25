pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'demo-cluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://3FAD0683C5D74A3120F8A884E99FC7AD.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'demo-cluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://3FAD0683C5D74A3120F8A884E99FC7AD.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
