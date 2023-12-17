pipeline{

    agent ('MAVEN')
    options{
                timeout(time: 10, unit: 'MINUTES')
            }
            triggers { 
                pollSCM('H */4 * * 1-5')
            }
    stages{
        stage('GIT'){
            steps{
                git url: https://github.com/yes-key/spring-petclinic.git, branch: dev
            }
        stage('build'){
        sh mvn 'mvn clean package'        
        }
    }
    }
 } 
