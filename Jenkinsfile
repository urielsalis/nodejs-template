pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        build job: '$template', propagate: true, parameters: [[$class: 'StringParameterValue', name: 'REPO', value: '$projectUrl'], [$class: 'StringParameterValue', name: 'NAME', value: "${env.JOB_NAME}-${env.BUILD_NUMBER}"]]      }
    }

    stage('Create AMI') {
      steps {
        build job: '$template-ami', propagate: true, parameters: [[$class: 'StringParameterValue', name: 'NAME', value: "${env.JOB_NAME}-${env.BUILD_NUMBER}"]]
      }
    }
  }
}
