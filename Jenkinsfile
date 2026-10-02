pipeline {
    agent any

    tools {
        maven 'MAVEN_HOME'
    }

    stages {
        stage('Clean') {
            steps {
                bat 'mvn clean'
            }
        }

        stage('Install') {
            steps {
                bat 'mvn install'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }
    }

    post {
        success {
            emailext(
                to: 'sanjanasamala6@gmail.com',
                subject: "Jenkins Build Successful: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """The Jenkins build was successful.

Job: ${env.JOB_NAME}
Build: #${env.BUILD_NUMBER}
Status: ${currentBuild.currentResult}
"""
            )
        }

        failure {
            emailext(
                to: 'sanjanasamala6@gmail.com',
                subject: "Jenkins Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """The Jenkins build failed.

Job: ${env.JOB_NAME}
Build: #${env.BUILD_NUMBER}
Status: ${currentBuild.currentResult}
"""
            )
        }
    }
}