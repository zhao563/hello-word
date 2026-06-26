pipeline {
    agent { docker { image 'openjdk:17-jdk-slim' } }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Compile & Run') {
            steps {
                sh '''
                    echo "=== Compiling ==="
                    javac src/main/java/Hello.java -d out/
                    echo "=== Running ==="
                    java -cp out/ Hello
                '''
                archiveArtifacts artifacts: 'out/**', fingerprint: true
            }
        }
    }
}