pipeline {
    agent any
    environment {
        PROJECT_ID = 'gcp-testing-services'
        CLUSTER_NAME = 'gkecluster-01'
        LOCATION = 'us-central1-a'
        CREDENTIALS_ID = 'gkecluster-sa01'
        DOCKER_HUB_USERNAME = 'ssonukumar28'
    }
    stages {
        stage("Checkout code") {
            steps {
                checkout scm
            }
        }
        stage('Deploy to GKE') {
            steps{
                step([$class: 'KubernetesEngineBuilder', projectId: env.PROJECT_ID, clusterName: env.CLUSTER_NAME, location: env.LOCATION, manifestPattern: 'nginx.yaml', credentialsId: env.CREDENTIALS_ID, verifyDeployments: true])
            }
        }
    }
}
