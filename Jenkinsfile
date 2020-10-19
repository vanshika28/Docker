pipeline {
  environment {
    registry = "vanshikagarg/devproject"
    registryCredential = 'vanshikagarg'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/vanshika28/Docker.git'
      }
    }
    stage('Build') {
       steps {
         sh 'docker build -t sysprjct .'
       }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Deploy Image') {
      steps{
         script {
            docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
 }
 }

