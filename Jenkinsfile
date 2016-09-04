node {
   // Mark the code checkout 'stage'....
   stage 'Checkout'

   // Get some code from a GitHub repository
   //git url: 'https://github.com/jglick/simple-maven-project-with-tests.git'
   git url: 'https://github.com/stuartcbrown/game-of-life.git'
   // Get the maven tool.
   // ** NOTE: This 'M3' maven tool must be configured
   // **       in the global configuration.           
   def mvnHome = tool 'M3'
   tool 'JDK8'
   env.JAVA_HOME="${tool 'JDK8'}"

   // Mark the code build 'stage'....
   stage 'Build'
   // Run the maven build
   sh "${mvnHome}/bin/mvn -Dmaven.test.failure.ignore clean package"
   stage 'Archive'
   echo 'running archive'
   step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml,**/target/test-results/TEST-*.xml'])
//input id: 'My Stuff', message: 'Input some stuff', ok: 'Press this', submitter: 'brown'
//  junit '**/build/test-reports/*.xml'  
}
