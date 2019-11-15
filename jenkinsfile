node("docker") {
    docker.withRegistry('https://hub.docker.com/repository/docker/sofianebrinis/', 'Bienvenue1') {

        git url: "https://github.com/sofianebrinis/docker-base-tester-behat.git", credentialsId: 'Bienvenue1'

        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id

        stage "build"
        def app = docker.build "your-project-name"

        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
