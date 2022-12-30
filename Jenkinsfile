pipeline{
    agent any
    tools{
        maven 'MAVEN'
    }
    stages{
        stage ('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to tomcat server') {
            steps{
                deploy adapters: [tomcat9(credentialsId: '24899974-cb74-4b5f-af4c-317d4da4f2f6', path: '', url: 'http://localhost:8060/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
