pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-Cluster-Microservices', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://F5086523811DBABA42A39389A8E5A64C.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-Cluster-Microservices', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://F5086523811DBABA42A39389A8E5A64C.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
