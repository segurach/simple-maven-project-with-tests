node ('master') {
   checkout scm
   def mvnHome
   mvnHome = tool 'M3'
   stage ('Build') {
       if (isUnix()) {
           sh '${mvnHome}/bin/mvn -Dmaven.test.failure.ignore clean package'
       }
   }
   stage ('Results') {
       junit '**/target/surefire-reports/TEST-*.xml'
       archive 'target/*.jar'
   }
}
