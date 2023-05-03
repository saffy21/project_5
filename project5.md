# CLIENT-SERVER ARCHITECTURE WITH MYSQL

## IMPLEMENT A CLIENT SERVER ARCHITECTURE USING MYSQL DATABASE MANAGEMENT SYSTEM (DBMS)

### Create and configure two Linux-based virtual servers EC2 instances in AWS

Server A name - `mysql server`
Server B name - `mysql client`

![creation of client and server instances](./image_5/creation_of_mysql_server_and_client_instances.png)

### update and upgrade for server

`sudo apt update`

`sudo apt upgrade`

![update](./image_5/sudo_apt_update.png)

![upgrade](./image_5/sudo_apt_upgrade.png)

### update and upgrade for client server

`sudo apt update`

![update client](./image_5/sudo_apt_update_client.png)

`sudo apt upgrade`

![upgrade client](./image_5/sudo_apt_upgrade_client.png)

### installing mysql server on server A

`sudo apt install mysql-server`

![installing mysql-server](./image_5/mysql_server_install.png)

`sudo mysql`

![login to mysql](./image_5/sudo_mysql.png)

`mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';`

`mysql> exit`

`sudo mysql_secure_installation`

![mysql secure installation](./image_5/mysql_secure_installation.png)

![mysql secure installation](./image_5/mysql_secure_installation_continued.png)

` mysql -u root -p`

![login to mysql](./image_5/login_to_mysql.png)

`mysql>  CREATE USER 'slushpuppy'@'%' IDENTIFIED BY 'senisafid3';`

`mysql> GRANT ALL PRIVILEGES ON * . * TO 'slushpuppy'@'%';`

`mysql>  FLUSH PRIVILEGES;`

![creating % user](./image_5/creating_a_new_%25_user_in_mysql.png)

`mysql>  select user,host from mysql.user;`

![checking user and host](./image_5/creating_a_new_%25_user_in_mysql.png)

`mysql> exit`

`sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf` in the bind address I replaced ‘127.0.0.1’ to ‘0.0.0.0’

![changing bind address](./image_5/changing_the_binding_address.png)

`:wqa`

`systemctl status mysql.service`

`sudo service mysql restart`

![checking status and restarting mysql](./image_5/checking_and_restarting_service.png)

### installing mysql client on server B

`sudo apt-get install mysql-client`

![mysql-client installation](./image_5/installing_mysql_client.png)

` mysql -u slushpuppy -h 172.31.1.10 -p`

![connecting to mysql server from mysql client](./image_5/connecting_mysql_server.png)

`mysql> Show databases;`
