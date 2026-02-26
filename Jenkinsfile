@Library("Shared") _
pipeline{
    agent { label "agent1"}
    
    stages{
        stage("Clone"){
            steps{
                script{
                    clone("https://github.com/sid0109/django-notes-app.git","main")
                }
            }
        }
        stage("Build"){
            steps{
                echo "Code Building"
                sh "docker build -t notes-app:latest ."
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app","latest","siddharth0109")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "code deploying..."
                sh "docker compose up -d"
                echo "code deployed!!!"
            }
        }
    }
}
