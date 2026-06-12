---
title: "Zoneminder Dapper Howto"
date: 2006-08-11
forum: General Help
---

### Post by BrownieMan on 2006-08-11
At long last I might have found the coveted howto for zoneminder on ubuntu. I just came across this right nwo and seems to have just been posted today on teh zoneminder site. I haven't tried it out yet, but hopefully it works.

"***Installing on Ubuntu (Dapper)

***Pre install tasks*******
sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install php5-mysql
sudo apt-get install libapache2-mod-auth-mysql
sudo apt-get install mysql-server
sudo apt-get install g++
sudo apt-get install libclass-manip-perl
sudo apt-get install libmysqlclient12-dev
sudo apt-get install libcurl3-openssl-dev
sudo apt-get install libjpeg-mmx-dev
sudo apt-get install liblwp-protocol-http-socketunix-perl

wget [http://www2.zoneminder.com/downloads/ZoneMinder-1.22.2.tar.gz](http://www2.zoneminder.com/downloads/ZoneMinder-1.22.2.tar.gz)

tar -xvzf ZoneMinder-1.22.2.tar.gz

cd ./ZoneMinder-1.22.2

*****Installation Tasks************
./configure --with-webdir=/var/www/zm --with-cgidir=/usr/lib/cgi-bin --with-webuser=www-data --with-webgroup=www-data

mysql mysql < db/zm_create.sql

mysql mysql

mysql> grant select,insert,update,delete on zm.* to 'zmuser'@localhost identified by 'zmpass';

mysql> quit

mysqladmin reload

make install

****Post Installation****
This next step is meant to make Zoneminder start on boot up however,
it doesn't do that yet. If anyone and let me know how that would be great.
****
cp ./ZoneMinder-1.22.2/scripts/zm /etc/init.d/zm

chmod +x /etc/init.d/zm
sudo apt-get install update-rc.d
sudo update-rc.d zm defaults"

---

### Post by robmoore on 2006-08-20
This works for me:

[http://www.zoneminder.com/wiki/index.php/Debian_init.d](http://www.zoneminder.com/wiki/index.php/Debian_init.d)

---

### Post by 1977hans on 2007-01-21
I just installed ZoneMinder 1.22.3 on Edgy, and i found this HOWTO useful. Thanks!

I have some information to share:

1) I think ```
sudo apt-get install libclass-manip-perl
``` is ment to be ```
sudo apt-get install libdate-manip-perl
```.

2) I used: ```
./configure  --with-lame=/usr/bin --with-ffmpeg=/usr/bin --with-mysql=/usr/bin --with-webdir=/var/www/zm --with-cgidir=/usr/lib/cgi-bin --with-webuser=www-data --with-webgroup=www-data
```

3) I think ```
mysql mysql < db/zm_create.sql
``` was ment to be ```
sudo mysql < db/zm_create.sql
```.

4) I think ```
mysql mysql
``` was ment to be ```
sudo mysql
```.

5) I've attached a patch for the startup script. Use:
```
cd /etc/init.d
sudo patch -p0 < <path>/zm_1.22.3_startup_script_ubuntu.patch.txt
``` to apply the patch.

6) By default Edgy uses */bin/dash* to run the zm startup script. This means an error message will be written when the startup script is running [1]. Making */bin/sh* point to */bin/bash* will work around this problem:
```
sudo rm /bin/sh
sudo  ln -s /bin/bash /bin/sh
```

[1] [http://diveintomark.org/archives/2006/09/19/bad-fd-number]("http://diveintomark.org/archives/2006/09/19/bad-fd-number")

I think that was all...

BR,
Hans

---

