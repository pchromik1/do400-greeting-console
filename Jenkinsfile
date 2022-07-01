pipeline{
    agent{
        label "nodejs"
    }
    stages{
        stage("Install dependencies"){
            steps{
                sh "npm ci"
            }
        }

        stage("Check Style"){
            steps{
                sh "npm run lint"
            }
        }

        stage("Test"){
            steps{
                sh "npm test"
            }
        }

        // Add the Release stage here
        stage('ReleAse') {
            steps{
                sh '''
                    oc project vzqiwk-greetings
                    oc start-build greeting-console --follow --wait
                '''
            }
        }
    }
}
