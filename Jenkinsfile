pipeline{
    tools{
        jdk 'myjava'
        maven 'mymaven'
    }
    agent none
    stages{
        stage('Checkout'){
            agent {label 'linux_slave'}
            steps{
                git 'https://github.com/onomzy2000/DevOpsClassCodes.git'
            }
            
        }
        stage('Compile'){
            agent {label 'linux_slave'}
            steps{
                git 'https://github.com/onomzy2000/DevOpsClassCodes.git'
                sh 'mvn compile'
            }
            
        }
        stage('CodeReview'){
            agent {label 'linux_slave'}
            steps{
                git 'https://github.com/onomzy2000/DevOpsClassCodes.git'
                sh 'mvn pmd:pmd'
            }
            
        }
        stage('UnitTest'){
            agent {label 'linux_slave'}
            steps{
                git 'https://github.com/onomzy2000/DevOpsClassCodes.git'
                sh 'mvn test'
            }
            
        }
        stage('MetricCheck'){
            agent {label 'linux_slave'}
            steps{
                git 'https://github.com/onomzy2000/DevOpsClassCodes.git'
                sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
            }
            post{
                always{
                    cobertura coberturaReportFile: 'target/site/cobertura/coverage.xml'
                }
            }
            
        }
        stage('Package'){
            agent {label 'linux_slave'}
            steps{
                git 'https://github.com/onomzy2000/DevOpsClassCodes.git'
                sh 'mvn package'
            }
            
        }
        
    }
}
