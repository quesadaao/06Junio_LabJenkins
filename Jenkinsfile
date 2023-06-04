pipeline {
    agent any
    stages {
        stage('Check Requirements') {
            steps {
                echo 'Unit tests!'
                sh 'junit --version'
            }
        }
        stage('Unit tests') {
            steps {
                echo 'Unit tests!'
                sh 'junit --version'
                sh 'make build test-unit'
                sh 'junit --version'
                archiveArtifacts artifacts: 'results/*.xml'
                archiveArtifacts artifacts: 'results/*.html'
            }
        }
        stage('Api tests') {
            steps {
                echo 'Api tests!'
                sh 'make build test-api'
                archiveArtifacts artifacts: 'results/*.xml'
                archiveArtifacts artifacts: 'results/*.html'
            }
        }
        stage('E2e tests') {
            steps {
                echo 'E2e tests!'
                sh 'make build test-e2e'
                archiveArtifacts artifacts: 'results/*.xml'
                archiveArtifacts artifacts: 'results/*.html'
            }
        }
    }
    post {
        always {
            junit 'results/*_result.xml'
            cleanWs()
        }
    }
}