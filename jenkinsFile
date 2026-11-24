pipeline{
    agent none
    stages{
        stage('build'){
            agent {
                label 'build-node'
            }
            steps{
                deleteDir()
                
                sh '''
                git clone https://github.com/zydashil-bot/my-portfolio.git
                ls -la
                '''
                stash name:'webpage',includes: 'my-portfolio/**'
            }
        }
        stage('deploy'){
            agent{
                label 'deploy-node'
            }
            steps{
                deleteDir()
                unstash 'webpage'
                sh '''
                sudo rm -rf /var/www/html/*
                sudo cp -r my-portfolio/* /var/www/html
                ls -la /var/www/html
                '''
            }
        }
    }
}
