# hometask aassignment

Task : to automate the process of integration of docker-git-jenkins

Steps involved:-

Repository:

1. Created a repository locally #hometask using #Git_Bash
2. Initialize #hometask and then created files #a.html and #b.html
3. Added these files to the #Staging_area using command: git add .
4. Connected #hometask repo to my #GitHub account using : git remote add "name" git_repo_url
5. Commited all files to Github repo using git command: git commit . -m "comment"
6. Created two branches #master and #dev1 using command: git branch branch_name and git push -u branch_name.
7. Created a #git_hook called #post-commit using #bash_script and pushed #b.html from #dev1 branch using git commit . -m comment

In Jenkins, I created jobs for different task:

Job1: #production_trigger1 and #production:

1. This will create a production environment
2. Used POLLSCM for making triggers to fetch data in every 1 min.
3. Connected with SCM using Git repository url.

Commands for environment creation:
        if sudo docker ps | grep prodenv
        then
        sudo docker rm -f prodenv
        sudo docker run -dit -p 1212:80 -v /dev:/usr/local/apache2/htdocs --name prodenv httpd
        else
        sudo docker run -dit -p 1212:80 -v /ishweb:/usr/local/apache2/htdocs --name prodenv httpd
        fi

Command for storing data which is fetched from github: sudo cp -rvf * /ishb

Job2: #dev_trigger1 and #developer:

1. This will create a testing environment name as new.
2. Used POLLSCM for making triggers to fetch data in every 1 min.
3. Connected with SCM using Git repository url.

Command for environment creation:
        if sudo docker ps | grep new
        then
        sudo docker rm -f new
        sudo docker run -dit -p 1213:80 -v /dev:/usr/local/apache2/htdocs --name new httpd
        else
        sudo docker run -dit -p 1213:80 -v /dev:/usr/local/apache2/htdocs --name new httpd
        fi

Command for storing data which is fetched from github: sudo cp -rvf * /dev

Job3: QAT team

1. Created job #QAT as trigger by build trigger using remote url and authentication token.
2. Setup the SCM using git url and provide credentials username and password.
3. Setup additional behaviours merge before build.
4. Used #Post-build_Action Git publisher.
