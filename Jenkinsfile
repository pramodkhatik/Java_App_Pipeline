pipeline{
agent any
stages {
    stage('Prepare Workspace'){
        steps{
            cleanWs()
        }
    }
    stage('Git Checkout'){
        steps{
            checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'Git-Jenkins', url: 'https://github.com/pramodkhatik/Java_App_Pipeline.git']])
        }
    }
    stage('Sonar Quality Check'){
        agent{
            docker {
                image 'maven'
            }
        }
        steps{
            script{
              withSonarQubeEnv(credentialsId: 'Sonar') {
                  sh 'mvn clean package sonar:sonar'
}
            }
        }
    }
}

}