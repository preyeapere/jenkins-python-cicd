pipeline{
    agent any
    stages{
         stage("GitHub checkout") {
            steps {
                script {
 
                    git branch: 'main', url: 'https://github.com/preyeapere/jenkins-python-cicd.git' 
                }
            }
        }
        stage("Build docker image"){
            steps{
                sh 'printenv'
                sh 'git version'
                sh 'docker build . -t preyeapere/pipeline-jenkinsimg'
            }
        }
         stage("push image to DockerHub"){
            steps{

               script {
                  
                 withCredentials([string(credentialsId: 'dockerID', variable: 'dockerID')]) {
                    sh 'docker login -u preyeapere -p ${dockerID}'
            }
              sh 'docker push preyeapere/pipeline-jenkinsimg:latest'
            }
        }
    }
    }
}