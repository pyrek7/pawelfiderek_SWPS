
pipeline {
    agent any
    environment {
       dotnet = '"C:\\Program Files\\dotnet\\dotnet.exe"'
       DEPLOY_TO = "main environment"
    }
        stages {
            stage('DeploymentSelection')
            {
                  when {
                        branch 'main'
                    }
                    steps{
                        echo "selected environment: ${DEPLOY_TO}"
                    }
            }
            stage('ScriptStage') {
                steps {
                    parallel (
                    "TaskOne" : {
                        echo 'task one stuff part 1'
                        echo 'task one stuff part 2'
                        echo 'task one stuff part 3'
                    },
                    "TaskTwo" : {
                        echo 'tasl two stuff part 1'
                        echo 'tasl two stuff part 2'
                    }
                    )
            }
            }
            stage('Build') {
                steps {
                   dir("pawelfiderek_SWPS"){
                    bat "${dotnet} build"
                   }
                }
            }
            stage('Test') {
                steps {
                    echo 'testy testy'
                   }
                }
            }
            stage('Clean') {
                steps {
                   dir("pawelfiderek_SWPS"){
                    bat "${dotnet} clean"
                   }
                }
            }
    }
