pipeline {
  agent any
  stages {
    stage('Compile') {
      steps {
        script{
                def mvnHome = tool name: 'maven', type: 'maven'
                sh "${mvnHome}/bin/mvn package"
        }
      }
    }
    stage('Building Docker Image') {
      steps{
        script {
          sh "docker build -t sudhagarmsr/cicd-poc-jenkins-ansible:$BUILD_NUMBER ."
        }
      }
    }
    stage('Push Image To Docker Hub') {
      steps{
        script {
          sh "echo $USER"
          sh "docker login -u sudhagarmsr -p sudhagarmsr@712"
          sh "docker push sudhagarmsr/cicd-poc-jenkins-ansible:$BUILD_NUMBER"
          }
        }
      }
    }
}

