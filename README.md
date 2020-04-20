# OpenVPN Admin

## Summary
Administrate its OpenVPN with a web interface (logs visualisations, users managing...) and a SQL database.

![Previsualisation configuration](https://lutim.cpy.re/fUq2rxqz)
![Previsualisation administration](https://lutim.cpy.re/wwYMkHcM)


## Prerequisite

  * GNU/Linux with Bash and root access
  * Fresh install of OpenVPN
  * Web server (NGinx, Apache...)
  * MySQL
  * PHP >= 5.5 with modules:
    * zip
    * pdo_mysql
  * bower
  * unzip
  * wget
  * sed
  * curl

### Debian 8 Jessie

````shell
$ apt-get install openvpn apache2 php5-mysql mysql-server php5 nodejs unzip git wget sed npm curl
$ npm install -g bower
$ ln -s /usr/bin/nodejs /usr/bin/node
````

### Debian 9 Stretch

In order to install `npm`, [stretch-backports need to be added to your sources.list](https://backports.debian.org/Instructions/#index2h2).

````shell
$ apt-get install -t stretch-backports npm nodejs
$ apt-get install openvpn apache2 php-mysql mysql-server php-zip php unzip git wget sed curl
$ npm install -g bower
````

### CentOS 7

````bash
$ yum install epel-release
$ yum install openvpn httpd php-mysql mariadb-server php nodejs unzip git wget sed npm php-zip
$ npm install -g bower
$ systemctl enable mariadb
$ systemctl start mariadb
````

### Centos 8

```shell
$ dnf install epel-release -y
$ sed -i 's|^#baseurl=https://download.fedoraproject.org/pub|baseurl=https://mirrors.aliyun.com|' /etc/yum.repos.d/epel*
$ sed -i 's|^metalink|#metalink|' /etc/yum.repos.d/epel*
$ dnf install php-json php-xml  php-mysqlnd php-mbstring  php-common  php-gd php-fpm php-zip php
$ dnf install openvpn nodejs unzip git wget sed npm net-tools
$ dnf install mariadb-server && systemctl enable mariadb && systemctl start mariadb
$ mysql_secure_installation
$ dnf install httpd -y && systemctl enable httpd && systemctl start httpd
$ npm install -g bower
$ mkdir ~/my_coding_workspace
```



### Other distribution... (PR welcome)

## Tests

Only tested on Debian Jessie. Feel free to open issues.

## Installation

  * Setup OpenVPN and the web application:

      ```shell
      $ cd ~/my_coding_workspace
      $ git clone https://github.com/Chocobozzz/OpenVPN-Admin openvpn-admin
      $ cd openvpn-admin
      $ ./install.sh /var/www apache apache
      $ systemctl enable openvpn-server@server
      ```
      

      
  * Setup the web server (Apache, NGinx...) to serve the web application.

  * Create the admin of the web application by visiting `http://your-installation/index.php?installation`

## Usage

  * Start OpenVPN on the server (for example `systemctl start openvpn@server`)
  * Connect to the web application as an admin
  * Create an user
  * User get the configurations files via the web application (and put them in */etc/openvpn*)
  * Users on GNU/Linux systems, run `chmod +x /etc/openvpn/update-resolv.sh` as root
  * User run OpenVPN (for example `systemctl start openvpn@client`)

## Update

    $ git pull origin master
    # ./update.sh /var/www

## Desinstall
It will remove all installed components (OpenVPN keys and configurations, the web application, iptables rules...).

    # ./desinstall.sh /var/www

## Use of

  * [Bootstrap](https://github.com/twbs/bootstrap)
  * [Bootstrap Table](http://bootstrap-table.wenzhixin.net.cn/)
  * [Bootstrap Datepicker](https://github.com/eternicode/bootstrap-datepicker)
  * [JQuery](https://jquery.com/)
  * [X-editable](https://github.com/vitalets/x-editable)
