pipeline {
 agent any

 stages {

 stage('Checkout') {
 steps {
 git branch: 'main',
 url: 'https://github.com/shri1224/8.2CDevSecOps.git'
 }
 }

 stage('Install Dependencies') {
 steps {
 sh 'npm install'
 }
 }

 stage('Run Tests') {
 steps {
 sh 'npm test || true'
 }
 }

 stage('Generate Coverage Report') {
 steps {
 sh 'npm run coverage || true'
 }
 }

 stage('NPM Audit (Security Scan)') {
 steps {
 sh 'npm audit || true'
 }
 }

 }

 post {

 always {

 emailext (
 subject: "Jenkins Build: ${currentBuild.currentResult}",

 body: """
 Build Status: ${currentBuild.currentResult}

 Project: ${env.JOB_NAME}
 Build Number: ${env.BUILD_NUMBER}

 Check Jenkins for full details.
 """,

 to: "shrikantsk1224@gmail.com",

 attachLog: true
 )

 }

 }

}