pipeline
{
    agent any
        stages
    {
        stage('Clone repository')
        {
            steps
            {
                checkout([$class:'GitSCM', branches:[[name:'*/main']], userRemoteConfigs:[[url:'https://github.com/tanishqyaduka/PES1UG21CS661_Jenkins.git']]])
            }
        }

        stage('Build')
        {
            steps
            {
                sh 'g++ ./main/xyz.cpp -o output' build 'PES1UG21CS661-1'
            }
        }

        stage('Test')
        {
            steps
            {
                sh './output' script
                {
                    def output = sh(script : './output', returnStdout : true).trim() echo "Output of xyz.cpp: ${output}"
                }
            }
        }

        stage('Deploy')
        {
            steps
            {
                echo 'Deploy'
                // sh 'non_existent_command_failure'
            }
        }
    }

    post
    {
        failure
        {
            echo 'Pipeline failed'
        }
    }
}
