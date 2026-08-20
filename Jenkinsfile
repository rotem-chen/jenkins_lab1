pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo '=====Build stage ======='
                sh 'echo "This is some data for the exercise" > app.txt '
                sh'cat app.txt'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Starting Test stage...'
                sh 'test -f app.txt'
                sh '''
                    if [ -f app.txt ]; then
                        echo "Test Passed: app.txt exists!"
                    else
                        echo "Test Failed: app.txt not found!"
                        exit 1
                    fi
                '''
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Starting Deploy stage...'
                sh 'mkdir deploy'
                sh'cd app.txt deploy/'
                sh 'ls deploy'

            }
        }
    }

    post {
            always {
                echo '===== Workspace Cleaning ====='
                cleanWs() 
            }
        }
}