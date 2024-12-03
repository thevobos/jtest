pipeline {
    agent any

    environment {
        PATH = "/opt/homebrew/bin:$PATH" // Node ve JDK'yı bulabilmesi için
    }

    stages {
        stage('Install Dependencies') {
            steps {
                script {
                    // Bağımlılıkları yükle
                    sh 'yarn install'
                }
            }
        }

        stage('Android Build') {
            steps {
                script {
                    // Android için build işlemi
                    sh './gradlew assembleRelease'
                }
            }
        }

        stage('iOS Build') {
            steps {
                script {
                    // iOS için build işlemi
                    sh 'npx react-native run-ios --configuration Release'
                }
            }
        }
    }

    post {
        always {
            // Build sonrası yapılacak işlemler
            echo 'Build finished!'
        }
    }
}

