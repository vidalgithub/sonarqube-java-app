pipeline{
    agent any
    options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
    }
    tools {
        maven '3.9.9'  // Name of your Maven installation 
    }
    stages{
       stage('Checkout') {
           steps {
               script {
                   checkout scm
               }
           }
       }      
       stage('Build'){
            steps{
                sh 'mvn clean package'
            }
         }
        stage('SonarQube analysis') {
//    def scannerHome = tool 'SonarScanner 4.0';
            steps{
                withSonarQubeEnv('sonarqube-10.7') { 
        // If you have configured more than one global server connection, you can specify its name
//      sh "${scannerHome}/bin/sonar-scanner"
                sh "mvn sonar:sonar"
                }
            }
        }
       
    }
}
