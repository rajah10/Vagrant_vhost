
setup vhost in vagrant, apache2 environment. create multiple local environment in a vagrant guest machine  

# How to add multiple virtual hosts in Vagrant environment ? 

  

You have to do setup in guest and host machine.  

  

## Guest machine  

### 1) Log in to your vagrant environment  

    vagrant ssh 

### 2) Copy or create a config file in /etc/apache2/sites-available/ directory 

### 3) Open the file 

    sudo nano create_file.conf 

### 4) Paste bellow code and change the server name, alias and document root according to yout information 

    <VirtualHost *:80> 

       ServerAdmin webmaster@example.com 

       ServerName  example.com 

       ServerAlias example.com 

       DocumentRoot /var/www/your_directory/ 

       ErrorLog ${APACHE_LOG_DIR}/error.log 

       CustomLog ${APACHE_LOG_DIR}/access.log combined 

       Options Indexes FollowSymLinks 

    </VirtualHost>  

### 5) Enable the file 

    sudo a2ensite create_file.conf 

### 6) Restart the server 

    sudo service apache2 restart  

  

## Host machine 

### 1) Open the hosts file 

( Linux  ) 

    cd /etc 

    sudo nano hosts  

    add guest machine ip address and server name 

        192.168.14.02 example.com 

       ( run ifconfig to get the guest ip address ) 
