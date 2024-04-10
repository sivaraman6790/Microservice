pipeline { 
    agent any

    stages {
        stage('Deploy to kubernets') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://AF55E96D90B59638F9786D1777D0F716.gr7.ap-south-1.eks.amazonaws.com']]) {
                sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
    }
    
    stages {
        stage('Verify deployment') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://AF55E96D90B59638F9786D1777D0F716.gr7.ap-south-1.eks.amazonaws.com']]) {
                sh "kubectl get svc -n webapps" 
            }
        }
    }
}
