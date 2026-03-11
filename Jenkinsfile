pipeline {
    agent any

    stages {
        stage('Deploy to k8s') {
            steps {
            withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' my-eks-cluster', contextName: '', credentialsId: 'k8s-cred', namespace: 'webapps', serverUrl: 'https://D3172BEBDB4A015541FE7050C1305433.gr7.ap-south-1.eks.amazonaws.com']]) {
               sh "kubectl apply -f deployment-service.yml"
}
            }
        }
        
         stage('verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' my-eks-cluster', contextName: '', credentialsId: 'k8s-cred', namespace: 'webapps', serverUrl: 'https://D3172BEBDB4A015541FE7050C1305433.gr7.ap-south-1.eks.amazonaws.com']]) {
                sh "kubectl get all -n webapps"
}
            }
        }
    }
}
