pipeline {
    agent any

    stages {
        stage('pull') {
            steps {
               checkout([$class: 'GitSCM', branches: [[name: '*/dev']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '7c622183-5741-4e78-a144-ad4b8d8230bc', url: 'https://github.com/wuyan9308/demo.git']]])
            }
        }
        stage('build') {
            steps {
              sh 'mvn clean package'
            }
        }
         stage('deploy') {
            steps {
              deploy adapters: [tomcat8(credentialsId: '932e9c9c-ec1c-45c0-ad3a-4d1657dc66ac', path: '', url: 'http://192.168.88.1')], contextPath: null, war: 'target/*.war'
            }
        }
    }
}
