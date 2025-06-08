pipeline{
  agent any
  tools{
    maven 'Maven'
  }
  stages{
    stage('checkout'){
      steps{
        git branch:'master',url:'https://github.com/srushtiiik/exmans.git'
      }
    }
  stage('build'){
    steps{
      sh 'mvn clean package'
    }
  }
  stage('Archive'){
    steps{
      archiveArtifacts artifacts: 'target/*.war',fingerprint:true
    }
  }
  stage('Deploy'){
    steps{
      sh 'mvn clean install'
      sh 'ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'
    }
  }
  }
}   
