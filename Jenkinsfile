pipeline {
    agent {
        label '!windows'
    }

    environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE    = 'sqlite'
    }

    stages {
        stage('SonarQube analysis') {
            steps {
                script {
                    // requires SonarQube Scanner 2.8+
                   scannerHome = tool 'SonarQubeScanner'
                }
                withSonarQubeEnv('SonarQube') {
                    sh 'printenv'
                    sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=test"
                }
            }
        }
    }
}
