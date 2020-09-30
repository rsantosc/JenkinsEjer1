pipeline{
    agent any
    
    tools{
        maven 'localMaven'
    }
    
    stages{
        stage ('package - Checkout') {
 	        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '', url: 'https://github.com/haschel/maven-project.git']]]) 
	    }
	    
        stage('Build'){
            steps{
              bat 'mvn clean package'      
            }
            
            post{
                success{
                    echo 'Estamos haciendo el archive de los artefactos...'
                    archiveArtifacts artifacts: '**/*.war'
                }
                
            }
            
        }
        
    }
}
