# Jenkins CI/CD


Pipeline script on Jenkins:
```
node {
    def mvnHome
    stage("Step 1 - Preparation") { // for display purposes
        // Get some code from a GitHub repository
        git 'https://github.com/viniciusabreusouza/Jenkins_CI_CD_Example.git';
    }
    stage("Step 2 - Docker Build") { // for display purposes
        // Get some code from a GitHub repository
        sh "sudo docker build -t htmlapp .";
    }
    stage("Step 3 - Stoping Application") { // for display purposes
        // Get some code from a GitHub repository
        sh label: '', script: 'sudo docker run hello-world;sudo docker stop $(sudo docker ps -a -q); sudo docker container prune -f'
    }
    stage("Step 4 - Deploy Application"){
        sh "sudo docker run --name htmlsite -p 8082:80 -d htmlapp";
    }
}

```

