pipeline { 
  agent any 
  options {
        skipStagesAfterUnstable()
        disableConcurrentBuilds()
  }
  stages {
     stage('Clone the repo') { 
       steps {
         script {
            //Extract the Pull Request branch name from the environment variables
           def pullRequestBranch = "main"

            //Clone the repository and checkout the Pull Request branch
           checkout([
             $class: 'GitSCM',
             branches: [
               [name: "*/main"]
             ],
             extensions: [
               [$class: 'CloneOption', depth: 1]
             ],
             userRemoteConfigs: [
               [
                 credentialsId: 'githubpat',
                 url: 'https://github.com/venkatzgithub/fluffy-telegram.git'
               ]
             ]
           ])
         }
       }
     }
    stage('PR') {
      steps {
        // sh 'cat Dockerfile'
       echo "ghprbTargetBranch: ${env.ghprbTargetBranch}"
      }
    }
  }
}
