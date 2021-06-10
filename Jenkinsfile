pipeline
{
agent any
environment
  {
    PATH='/sbin:/bin:/usr/sbin:/usr/bin:~/.local/bin/'
  }
  stages
  {
    stage('Install Pcluster if not present')
    {
      steps
      {
       sh 'pip-3.7 install aws-parallelcluster==2.10.2 --user'
      }
    } 
    

    stage('Create or Update Cluster with the Config file')
    {
      steps
      {
        script 
        {
            try 
            {
                sh 'pcluster create -c config divinescluster'
            } 
            catch (Exception e) 
            {
                echo 'Exception occurred: ' + e.toString()
                sh 'pcluster update -c config divinescluster -y'
            }
        }
        
      }
    }
  }
}
