pipeline {
  
  agent {
    label 'agent_java_docker'
  }
  
  stages {
    stage('Test u'){
      steps {
        sh 'mvn test'
      }
    }
    
    stage ('Compilation') {
      steps {
        sh 'mvn -B -DskipTests clean package'
      }
    }
    
    stage('Publication du binaire') {
      steps {
        sh "curl -u admin:0000 --upload-file /home/jenkins/test_maven/target/test_maven-1.0-SNAPSHOT.jar 'http://10.10.20.31:8081/repository/helloworld/helloworld${BUILD_NUMBER}.war'"        
      }
    }
    
  }
}
