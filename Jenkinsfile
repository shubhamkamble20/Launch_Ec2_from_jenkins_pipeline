pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID = credentials('AKIA3FLDZY472CUFK6RE')
        AWS_SECRET_ACCESS_KEY = credentials('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')
        AWS_DEFAULT_REGION = 'us-west-1'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from version control
                git 'https://github.com/your-repo/terraform-ec2'
            }
        }

        stage('Install Terraform') {
            steps {
                // Install Terraform
                sh 'wget https://releases.hashicorp.com/terraform/1.3.7/terraform_1.3.7_linux_amd64.zip'
                sh 'unzip terraform_1.3.7_linux_amd64.zip'
                sh 'mv terraform /usr/local/bin/'
            }
        }

        stage('Terraform Init') {
            steps {
                // Initialize Terraform
                sh 'terraform init'
            }
        }

        stage('Terraform Plan') {
            steps {
                // Plan Terraform execution
                sh 'terraform plan'
            }
        }

        stage('Terraform Apply') {
            steps {
                // Apply Terraform configuration
                sh 'terraform apply -auto-approve'
            }
        }
    }

    post {
        always {
            // Clean up the workspace after the build
            cleanWs()
        }
    }
}
