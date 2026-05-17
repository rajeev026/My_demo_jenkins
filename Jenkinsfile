pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Build stage'
                sh 'docker build -t myjenkinsapp .'
            }
        }

        stage('Test') {
            steps {
                echo 'Test stage'
                sh 'docker images | grep myjenkinsapp'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy stage'
                sh '''
                docker stop myjenkinsapp || true
                docker rm myjenkinsapp || true
                docker run -d -p 5000:5000 --name myjenkinsapp myjenkinsapp
                '''
            }
        }
    }
}
