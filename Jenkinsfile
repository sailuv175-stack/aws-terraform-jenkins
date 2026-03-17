pipeline {
  agent any

  environment {
    AWS_DEFAULT_REGION = 'us-east-1'
  }

  stages {

    stage('Checkout Code') {
      steps {
        echo 'Cloning repository...'
        git branch: 'main',
            url: 'https://github.com/YOUR-USERNAME/aws-terraform-jenkins.git'
      }
    }

    stage('Terraform Init') {
      steps {
        echo 'Initializing Terraform...'
        sh 'terraform init'
      }
    }

    stage('Terraform Validate') {
      steps {
        echo 'Validating Terraform files...'
        sh 'terraform validate'
      }
    }

    stage('Terraform Plan') {
      steps {
        echo 'Planning infrastructure changes...'
        sh 'terraform plan -out=tfplan'
      }
    }

    stage('Terraform Apply') {
      steps {
        echo 'Applying infrastructure...'
        sh 'terraform apply -auto-approve tfplan'
      }
    }

  }

  post {
    success {
      echo 'Infrastructure deployed successfully!'
    }
    failure {
      echo 'Pipeline failed. Check logs above.'
    }
  }
}
