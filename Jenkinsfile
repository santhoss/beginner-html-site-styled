pipeline {
  agent {
    kubernetes {
      yaml'''
      apiversion: v1
      kind:pod
      spec:
        containers:
        - name: linux
           image: apline:latest
           command:
           - cat
           tty: true
        '''
    }
  }

  environment {
    DOCKER_HUB_REPO = "santhoss/new-project0"
    KUBERNETES_DEPLOYMENT = "deployment.yml"
    KUBERNETES_SERVICE = "service.tml"
  }

  stages {
    stage('Build docker image0')
      steps {
        script {
          dockerimage = docker.build(""${DOCKER_HUB_REPO}:latest")
                                     }
                                     }
                                     }

      stage ('Push to DockerHub') {
        steps {
            script {
              docker.withRegistry('https://index.docker.io/v1','dockerhub_credentials') {
                  dockerimage.push()
              }
              }
        }
      }
      stage ('Deploy to Kubernetes') {
        steps {
          sh 'kubectl apply -f ${KUBERNETES_DEPLOYMENT}'
          sh 'kubectl apply -f ${KUBERNETES_SERVICE}'
        }
      }
   }   
   poset {
       success  {
           echo ' Deployment Successsful'
       }
       failyre {
         echo 'Deployment failed !
       }
   }
                                     }
                                     
