pipeline {
    agent any
    stages {
        stage ('git clone') {
            steps {
                git credentialsId: 'git', url: 'https://github.com/saivanapalli29/game.git'
            }
        }
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn test'
                }
            }
        }
        stage ('clean package') {
            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn clean package'
                }    
            }
        }


        stage ('Deployment Stage') {
            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn deploy'
                }
            }
        }
    }
}
