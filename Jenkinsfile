pipeline {
 environment {
 registry = "rajlocuz/poc-ca"
 registryCredential = 'rajlocuz-dockerhub'
 dockerImage = ''
 }
 agent any
 stages {
 stage('Cloning Git') {
 steps {
 git 'git@github.com:rajlocuz/sample-webapp.git'
 }
 }
 stage('Building Docker Image') {
 steps{
 script {
 dockerImage = docker.build registry + ":$BUILD_NUMBER"
 }
 }
 }
 stage('Push Image to Docker Hub') {
 steps{
 script {
 docker.withRegistry( '', registryCredential ) {
 dockerImage.push()
 dockerImage.push('latest')
 }}
 }}
 }
}
