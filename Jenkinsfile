pipeline {
    agent { label 'linux' }
    tools {
      maven 'Maven-3.8.4'
    }
    stages {
        stage('Source') {
            steps {
                sh 'mvn --version'
                sh 'git --version'
                git branch: 'master',
                    url: 'https://github.com/r-ali-ashik/jenkins-ssh-agent.git'
            }
        }
        stage('Clean') {
            steps {
                dir("${env.WORKSPACE}"){
                    sh 'mvn clean'
                }
            }
        }
        stage('Test') {
            steps {
                dir("${env.WORKSPACE}"){
                    sh 'mvn test'
                }
            }
        }
        stage('Package') {
            steps {
                dir("${env.WORKSPACE}"){
                    sh 'mvn package -DskipTests'
                }
            }
        }
    }
}
