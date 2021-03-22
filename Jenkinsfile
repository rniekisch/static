pipeline {
  agent any
  stages {
  
    // Linter
    stage('Lint HTML') {
      steps {
        sh 'tidy -q -e *.html'
      }
    }

    // Upload to AWS S3 bucket
    stage('Upload to AWS') {
      steps {
        withAWS(region:'us-west-2', credentials:'aws-static') {
          s3Upload(file:'index.html', bucket:'udc-pipeline-project-s3')
        }
      }
    }
  
  }
}