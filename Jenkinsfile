pipeline {
  agent {
     any {
      defaultContainer 'kaniko'
      yamlFile "jenkins-pod.yaml"
    }
  }
  environment {
    PROJECT = "jenkins-demo"
    REGISTRY_USER = "sagark24"
  }
  stages {
    stage("Build") {
      steps {
        container('kaniko') {
          sh "/kaniko/executor --context `pwd` --destination sagark24/jenkins-demo:latest --destination ${REGISTRY_USER}/${PROJECT}:${env.BRANCH_NAME.toLowerCase()}-${BUILD_NUMBER}"
        }
      }
    }
  }   
}
