pipeline{

  agent {
    kubernetes {
      yaml """
apiVersion: v1
kind: Pod
metadata:
  labels:
    some-label: some-label-value
spec:
  containers:
  - name: ruby
    image: ruby:2.5.1
    command:
    - cat
    tty: true
"""
    }
  }
    stages{
        stage("check version"){
            steps{
                sh 'ruby --version'
            }
        }
        stage("Clone"){
            steps{
            checkout scm
            }
        }

        stage("requirement"){
            steps{
                sh 'gem install bundler'
            }
        }
            stage("build"){
                steps{
                  sh 'bundle install'
                  sh 'bundle exec rake db:migrate'
                }
                
            }

            stage("Test"){
                steps{
                 echo 'testing'
                }
                
                

            }
    }
}