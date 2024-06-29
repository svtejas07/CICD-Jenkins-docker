pipeline {
    agent {
        docker {
            image 'maven:3.6.3-jdk-8' 
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                git 'https://your-repo-url.git'
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('my-app:latest')
                }
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker run -d -p 8080:8080 my-app:latest'
            }
        }
    }
}

