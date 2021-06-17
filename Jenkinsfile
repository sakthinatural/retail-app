pipeline {
    agent { label "${label}" }

    tools {
        maven "M3"
    }

    stages {
        stage('prep') {
            steps {
                git branch: 'main', url: 'https://github.com/qf-demoapp/retail-app.git'
            }
        }
        stage('build') {
            steps {
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }
           post {
               success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}
