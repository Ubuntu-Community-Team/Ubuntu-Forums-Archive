---
title: "Torrent box"
date: 2014-02-11
forum: General Help
---

### Post by tage2 on 2014-02-11
I'm trying to set up a ubuntu "torrent box" , 
*samba file sharing 
*transmission remote
*torrentwatchX  and this is where I am stuck, 

what I have done so far is 
[COLOR=#BBBBBB][FONT=Monaco][FONT=inherit][FONT=inherit][FONT=inherit]
[/FONT][/FONT][/FONT][/FONT][/COLOR]sudo apt-get install php-services-json php5-curl php5-cgi
[COLOR=#BBBBBB][FONT=Monaco][FONT=inherit][FONT=inherit]
[/FONT][/FONT][/FONT][/COLOR]cd ~/Downloads[COLOR=#BBBBBB][FONT=Monaco][FONT=inherit][FONT=inherit]
[/FONT]
[/FONT][/FONT][/COLOR]wget [http://torrentwatch-x.googlecode.com/files/TorrentWatchX-0.8.9.tar.gz](http://torrentwatch-x.googlecode.com/files/TorrentWatchX-0.8.9.tar.gz) -O torrentwatch-x.tar.gz[COLOR=#BBBBBB][FONT=Monaco][FONT=inherit][FONT=inherit]
[/FONT]
[/FONT][/FONT][/COLOR]tar xzvf ./torrentwatch-x.tar.gz
[COLOR=#BBBBBB][FONT=Monaco][FONT=inherit][FONT=inherit]
[/FONT][/FONT][/FONT][/COLOR]sudo mv ./TorrentWatchX-0.8.9/ /var/www/torrentwatch-x/
[COLOR=#BBBBBB][FONT=Monaco][FONT=inherit][FONT=inherit]
[/FONT][/FONT][/FONT][/COLOR]sudo cp /var/www/torrentwatch-x/php/config.php.dist /var/www/torrentwatch-x/php/config.php
[COLOR=#BBBBBB][FONT=Monaco][FONT=inherit][FONT=inherit]
[/FONT][/FONT][/FONT][/COLOR]sudo mkdir /etc/torrentwatch[COLOR=#BBBBBB][FONT=Monaco][FONT=inherit][FONT=inherit]

[/FONT]
[/FONT][/FONT][/COLOR]
and this I  believe installed torrentwatch? altso Installed Apache2 that I think is required to get this working

[FONT=monospace]sudo apt-get install apache2[/FONT] 

edited httpd.conf with 
 
sudo nano /etc/apache2/httpd.conf

and wrote /var/www/torrentwatch-x/web 

saved

and that is how far i have come , Please help me with  what I'm missing/ have done wrong to get this working

---

### Post by tage2 on 2014-02-11
I have 

sudo nano /etc/apache2/conf.d/torrentwatch-x.conf

[COLOR=#666666][FONT=Consolas]# Ensure Apache listens on port 9092[/FONT][/COLOR]
[COLOR=#666666][FONT=Consolas]Listen 9092[/FONT][/COLOR]
[COLOR=#666666][FONT=Consolas] [/FONT][/COLOR]
[COLOR=#666666][FONT=Consolas]# Listen for virtual host requests on all IP addresses[/FONT][/COLOR]
[COLOR=#666666][FONT=Consolas]NameVirtualHost *:9092[/FONT][/COLOR]
[COLOR=#666666][FONT=Consolas] [/FONT][/COLOR]
[COLOR=#666666][FONT=Consolas]<Directory "/var/www/torrentwatch-x">[/FONT][/COLOR]
[COLOR=#666666][FONT=Consolas] AllowOverride None[/FONT][/COLOR]
[COLOR=#666666][FONT=Consolas] AuthType Basic[/FONT][/COLOR]
[COLOR=#666666][FONT=Consolas] AuthName "TorrentWatch-X"[/FONT][/COLOR]
[COLOR=#666666][FONT=Consolas] AuthUserFile /etc/torrentwatch/passwords[/FONT][/COLOR]
[COLOR=#666666][FONT=Consolas] Require user admin[/FONT][/COLOR]
[COLOR=#666666][FONT=Consolas] Order Allow,Deny[/FONT][/COLOR]
[COLOR=#666666][FONT=Consolas] Allow from all[/FONT][/COLOR]
[COLOR=#666666][FONT=Consolas]</Directory>[/FONT][/COLOR]
[COLOR=#666666][FONT=Consolas] [/FONT][/COLOR]
[COLOR=#666666][FONT=Consolas]<VirtualHost *:9092>[/FONT][/COLOR]
[COLOR=#666666][FONT=Consolas] ServerName hoth.local[/FONT][/COLOR]
[COLOR=#666666][FONT=Consolas] DocumentRoot /var/www/torrentwatch-x[/FONT][/COLOR]
[COLOR=#666666][FONT=Consolas]</VirtualHost>[/FONT][/COLOR]

---

### Post by tage2 on 2014-02-11
altso did 
sudo nano /etc/torrentwatch/torrentwatch.config

and entered:

[Settings]


Episode Only = 0


Combine Feeds = 1


Transmission Login =


Transmission Password =


Transmission Host = localhost


Transmission Port = 9091


Transmission URI = /transmission/rpc


Watch Dir =


Download Dir = /home/torrents/download


Cache Dir = /var/www/torrentwatch-x/rss_cache/


TVDB Dir = /var/www/torrentwatch-x/tvdb_cache/


Save Torrents =


Run Torrentwatch = True


Client = Transmission


Verify Episode = 1


Only Newer = 1


Download Proper =


Default Feed All =


Deep Directories = 0


Require Episode Info = 1

---

### Post by tage2 on 2014-02-11
my sources if anybody cares :
[https://code.google.com/p/torrentwatch-x/wiki/Installation](https://code.google.com/p/torrentwatch-x/wiki/Installation)
[http://www.the-little-things.net/blog/2011/09/11/linux-headless-ubuntu-torrent-home-server/](http://www.the-little-things.net/blog/2011/09/11/linux-headless-ubuntu-torrent-home-server/)
[http://slovenly.wordpress.com/2010/02/02/setup-torrentwatch-x-with-transmission-on-openfiler/](http://slovenly.wordpress.com/2010/02/02/setup-torrentwatch-x-with-transmission-on-openfiler/)

---

### Post by tage2 on 2014-02-13
Nobody here knows how to get this up and running?
Or have any tips for other forums where i might get help?
want to use torrenwtatchx because i tried this on my popcorn hour, and this has been the best rss torrent fetcher i have tried,
unfortunately all the apps on the pch keep't crashing so want to get this up and running on ubuntu so it'll be reliable

---

