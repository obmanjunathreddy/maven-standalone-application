
node('master'){  
    
    def mavenHome=tool name: "mavenv3.1.1.1", type: "maven"
    
 stage('Checkout the code') {
   git branch: 'master', credentialsId: '4d6512c4-c101-4f43-aac5-5860f5d9e20c', url: 'https://github.com/MithunTechnologiesDevOps/maven-web-application.git'  
 }
 
 stage('Build')
 {
  sh  "${mavenHome}/bin/mvn clean package"
 }
 
 stage('SonarQube Report')
 {
  sh  "${mavenHome}/bin/mvn sonar:sonar"
 }
   
  
  stage('Upload Artifacts into Nexus')
 {
  sh  "${mavenHome}/bin/mvn deploy"
 }
 
 stage('DeplotoTomcat'){
     
     sh "cp $WORKSPACE/target/*.war /opt/apache-tomcat-9.0.16/webapps/"
 }
}
