pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git(url: 'https://github.com/santosh52krishna/gitlearn.git', branch: 'master')
      }
    }
    stage('build') {
      steps {
        sh 'mvn clean install'
      }
    }
    stage('test') {
      parallel {
        stage('test') {
          steps {
            sh 'mvn test'
          }
        }
        stage('ui test') {
          steps {
            sh 'mvn junit'
          }
        }
      }
    }
    stage('deploy') {
      steps {
        sh 'mvn clean deploy'
      }
    }
  }
}