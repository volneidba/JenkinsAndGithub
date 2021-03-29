pipeline {
  agent any 
  parameters {
    choice(name: 'VERSION',choices: ['1.1.10', '1.1.20', '1.1.30'], description: '')
    booleanParam(name: 'executeTests', defaultValue: true, description: '')
  }
  environment {
    NEW_VERSION = '1.10'
    }
  stages {
    stage("build") {
      when {
        expression {
          BRANCH_NAME =='main'
        }
      }  
      steps {
        echo 'building the application...'
        echo 'building version ${NEW_VERSION}'
      }
    }
    stage("test") {
      when {
        expression {
          BRANCH_NAME =='dev' || BRANCH_NAME == 'main'
        }
      }  
      steps {
        echo 'testing the application...'
      }
    }
    stage("deploy") {
      when {
        expression {
           params.executeTests
        }  
      }  
      steps {
        echo 'deploying the application...'
        echo "deploying version ${params.VERSION}"
      }
    }
  }
 }  
