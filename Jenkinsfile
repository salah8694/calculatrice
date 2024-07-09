pipeline {
    agent any
     
    tools { 
        nodejs "NodeJS"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/salah8694/calculatrice.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker build -t calculatrice .'
                sh 'docker run -d -p 5173:5173 calculatrice'
            }
        }
    }
}
