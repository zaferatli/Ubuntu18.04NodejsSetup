
# Ubuntu 18.04 Nodejs Backend Setup

I use followed commands for setup our Ubuntu 18.04 server for host phpmyadmin, mysql, nodejs.


## Commands

```js
sudo apt update
sudo apt install apache2
sudo apt install mysql-server
sudo systemctl start mysql.service
sudo mysql
	ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'yourmysqlpassword';
	exit
mysql -u root -p
sudo apt install phpmyadmin php-mbstring php-gettext
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh |  bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"
nvm install 16.15.1
sudo nano /etc/apache2/apache2.conf
	// Add Bottom
		Include /etc/phpmyadmin/apache.conf
sudo systemctl restart apache2.service
sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
	//127.0.0.1 to 0.0.0.0 
	//Mysql to root user previgle
	GRANT ALL PRIVILEGES ON *.* TO root@'%' IDENTIFIED BY 'yourmysqlpassword;
	FLUSH PRIVILEGES;

sudo nano +613 /usr/share/phpmyadmin/libraries/sql.lib.php
	//Phpmyadmin red alert when query
	|| (count($analyzed_sql_results['select_expr'] == 1) //from
	|| (count($analyzed_sql_results['select_expr']) == 1) //To

	&& ($analyzed_sql_results['select_expr'][0] == '*'))) //From
	&& ($analyzed_sql_results['select_expr'][0] == '*')) //To
	//Save Exit

sudo timedatectl set-timezone Europe/Istanbul
sudo service apache2 restart
sudo systemctl restart mysql
sudo apt install git
git clone https://youtgithubrepourl.com
cd ProjectName
npm install
npm install -g --save forever
npm install -g --save nodemon
```

