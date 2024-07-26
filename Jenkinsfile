pipeline {
    agent any

    environment {
        // Set your GitHub repository URL and credentials ID
        GITHUB_REPO_URL = 'https://github.com/sachinsachu96/html-sample-app.git'
        GITHUB_CREDENTIALS_ID = 'github'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the GitHub repository
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/master']],
                    doGenerateSubmoduleConfigurations: false,
                    extensions: [],
                    userRemoteConfigs: [[
                        url: "${GITHUB_REPO_URL}",
                        credentialsId: "${GITHUB_CREDENTIALS_ID}"
                    ]]
                ])
            }
        }

    stage('pull changes') {
            steps {
                script {
                    // Perform Git operations
                    sh '''
                        git pull origin master --ff
                    '''
                }
            }
        }
    }
}
