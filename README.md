Project 6: Linux Server Configuration and App Deployment
====================================
This project is about configuring a linux server using a Virtual Private Server (VPS) to serve a [web application](https://github.com/suffianhamzah/udacity-fsnd-project4) created using Flask.

# Server details
ip: 34.213.25.167
ssh port: 2200
URL: http://ec2-34-213-25-167.us-west-2.compute.amazonaws.com/

# Software installed

#### Ubuntu packages installed ```apt-get```
```bash
 $ sudo apt-get install python3-pip python3-setuptools apache2 libapache2-mod-wsgi-py3 postgresql postgresql-contrib git
 ```
 - python3-setuptools : To be able to use setuptools such as easy_install
 - python3-pip : The python3 version of ```pip```, a python package manager
 - apache2: Web server software
 - libapache2-mod-wsgi-py3: Python 3 WSGI adapter module for Apache aka the glue between python code and Apache web server
 - postgresql - Postgresql database for Ubuntu
 -  postgresql-contrib - Some extra packages for postgresql
 -  git - Git

 # Configuration changes done
 
 #### For setting up Server
 1. Secured server by only allowing Key-based authentications
 2. Set up Firewall - Only allow access to HTTP, NTP and SSH ports to be accessed remotely.

 #### For serving Flask
 1. Postgresql - Created user ```catalog``` that can only access the application database. Create database called ```catalog```
 2. Cloned the project using ```git clone``` into a directory, downloaded the python packages using ```pip install -r requirements.txt```, and ran ```python manage.py createdb``` to set up tables and some data into ```catalog``` database.
 3. Apache2 - Created a new config file, ```CatalogApp.conf``` for serving the Flask application. This includes setting up the serverName, ServerAdmin, wsgi settings (app directory, process name etc) and setting for preventing Apache from serving any files prefixed with ```.git``` 
 4. wsgi - Set up a ```.wsgi``` file which is a script to run the application app. This includes setting up the environment variables and adding the directory containing the application files into $PATH. 

 # List of references
 - How to prevent .git from being served https://serverfault.com/questions/128069/how-do-i-prevent-apache-from-serving-the-git-directory
 - Deploying Flask on VPS https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps
 - Setting up Environment Variables for WSGI https://www.pythonanywhere.com/forums/topic/963/
 - Help with virtualenv - https://stackoverflow.com/questions/42050982/flask-wsgi-no-module-named-flask
 - Help with Environment Variables https://gist.github.com/GrahamDumpleton/b380652b768e81a7f60c
 - Setting up mod-wsgi for Python 3 https://stackoverflow.com/questions/21158918/django-mod-wsgi-psycopg2-improperlyconfigured-error-loading-psycopg2-module
 - Set timezone for UTC https://askubuntu.com/questions/138423/how-do-i-change-my-timezone-to-utc-gmt
 - Setting up and securing database - https://www.digitalocean.com/community/tutorials/how-to-secure-postgresql-on-an-ubuntu-vps
 - Some help with getting Lightsail's public IP address - https://discussions.udacity.com/t/public-ip-for-google-oauths-authorized-redirect-uris/20341


