pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                sh """
                    cd /var/www/html/ssldash  # Replace with your directory
                    git pull origin main
                """
            }
        }
        // Optional stages for build and testing (modify as needed)
        // stage('Build') {
        //     steps {
        //         // Your build commands here (e.g., composer install, npm install)
        //     }
        // }
        // stage('Test') {
        //     steps {
        //         // Your test commands here (e.g., ./your_test_script.sh)
        //     }
        // }
        stage('Deploy to Server') {
            steps {
                script {
                    sh """
                        cd /var/www/html/ssldash  # Replace with your directory
                        cp -r /var/www/html/ssldash/* .  # Replace with source of your application files
                        sudo chown -R www-data:www-data *  # Set ownership for web server
                        sudo systemctl restart php8.1-fpm nginx  # Restart services
                    """
                }
            }
        }
    }
}
