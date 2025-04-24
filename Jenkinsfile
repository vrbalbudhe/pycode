pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/vrbalbudhe/pycode'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("pycode:latest")
                }
            }
        }

        stage('Run Tests') {
            steps {
                sh 'echo "Run your test command here"'
            }
        }

        stage('Push to DockerHub') {
            steps {
                withDockerRegistry(credentialsId: 'dockerhub-creds') {
                    script {
                        docker.image("pycode:latest").push('latest')
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                sh 'echo "Deploy using docker-compose or kubectl apply -f"'
            }
        }
    }
}
