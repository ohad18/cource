node{
  
  def mvnHome
  stage('Preparation') {
      cleanWs()

      // Get some code from a GitHub repository
      git 'git@github.com:omrisiri/course.git';
      // Get the Maven tool.
      mvnHome = tool 'M3'
   }
   
   
   stage ('create package'){
           sh "${mvnHome}/bin/mvn package"
   }
   
   
   stage ('Build Dockerfile'){
       
       sh 'docker build -t omrisiri/time-tracker:1 .'
       
   }
   stage ('ansible-push'){
     sh 'ansible-playbook /home/ubuntu/docker_push_playbook.yml -i /home/ubuntu/hosts'
   }
   stage ('ansible-pull and run'){
    sh 'ansible-playbook /home/ubuntu/docker_pull_run_playbook.yml -i /home/ubuntu/host'
   }
   
}
