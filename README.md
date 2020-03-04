# WSL-Lamp
 NSCC Student Ubuntu LAMP Stack Installation for Windows Subsystem for Linux

## Get WSL
* start>Run>appwiz.cpl
* turn Windows Features On...
* select Windows Subsystem fpr Linux
* ![Enable Feature](https://github.com/redmondmj/WSL-Lamp/blob/master/images/wsl-Install.PNG)
* or via powershell `Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
`

---

## Get Ubuntu Server
* vist the Microsoft Store
* choose your disired build and install
* ![Install App](https://github.com/redmondmj/WSL-Lamp/blob/master/images/store-Install.PNG)
* launch the app and create a local username and password

---

## Installing LAMP 
* update apt package manager `sudo apt update`
* (optional)install updates `sudo apt upgrade`
* (optional) install full stack:
    * `sudo apt install tasksel`
    * `sudo tasksel install lamp-server`

### Install Apache
* install apache2 package `sudo apt install apache2`
* note dependancies are automatically installed
* start the server `sudo service apache2 start`
* check the server status `sudo service apache2 status`
* test install by visiting [http://localhost](http://localhost) in your browser
* ![Install App](https://github.com/redmondmj/WSL-Lamp/blob/master/images/apache-Itworks.PNG)

### Install PHP
* install the package (version may vary) `sudo apt install php7.2`

### Install mysql or mariaDB
* install the package (mysql-server or mariadb-server) `sudo apt install mysql-server`
* start the service `sudo service mysql start`
* if mysql, then
   * (optional)run the configureation script `sudo mysql_secure_installation`
       * choose no for validation and set password for root
       * choose no for all options except "Reload privilege tables now?"
   * run mysql client `sudo mysql`
   * enable native passwords `ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';`
   * confirm native password enabled for root `SELECT user,authentication_string,plugin,host FROM mysql.user;`
   * exit
   * note to access mysql you now need to provide the root password `sudo mysql -p`

### Install phpmyadmin
* it's worth noting that this is just a web app and can be depoloyed manually as well
* install the package `sudo apt install phpmyadmin`
* IMPORTANT! press space to select apache2 as you web server
* ![Configure phpmyadmin](https://github.com/redmondmj/WSL-Lamp/blob/master/images/config-phpmyadmin.PNG)
* accept defaults for DB creation
* set phpmyadmin password
* start/restart apache `sudo apache2 start`
* login via browser [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

---

## Stopping the WSL 
* WSL runs under the LxssManager service
* it can be shut down via services
* ![stop WSL](https://github.com/redmondmj/WSL-Lamp/blob/master/images/wsl-stopservice.PNG)
* or via powershell `stop-service LxssManager`

---

## Start Over
* you can reset your Ubuntu instance by resetting it
* Apps & Features > Ubuntu 18.04?> Advanced Options
* Select Reset
* ![reset WSL](https://github.com/redmondmj/WSL-Lamp/blob/master/images/wsl-resetUbuntu.PNG)
