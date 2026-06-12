---
title: "Installing MediaWiki on Ubuntu"
date: 2005-04-24
forum: General Help
---

### Post by wiseleyb on 2005-04-24
Hopefully this is helpful to someone.  I'm a complete linux newbie.  After a fresh install of ubuntu on xp running in vmware this is what I needed to do to get MediaWiki running... note:  I have no clue what I'm doing ... this is probably fubar'd beyond belief - but it worked.

==LAMP (Linux Apache MySql PHP)==
sudo apt-get install apache2 mysql-server php4
	from [this thread](http://www.ubuntuforums.org/showthread.php?t=22029&highlight=mysql.so)  specifically [this post](http://www.ubuntuforums.org/showpost.php?p=106632&postcount=8) by [Azz!](http://www.ubuntuforums.org/member.php?u=844) (thanks man!)


untar [mediawiki](http://sourceforge.net/projects/wikipedia)  (right click the file on your desktop and open with archive manager

move the folder (note: start paying attention to directory names here - this will likely be different on your system)
$  cd /
$  cd var/www
$  sudo cp -r ../../home/wiseley/Desktop/mediawiki-1.4.2 mediawiki

change permissions
$  cd mediawiki
$  sudo chmod o+w config

Try the URL:
	[http://localhost/mediawiki/index.php](http://localhost/mediawiki/index.php)

If got a "couldn't load mysql.so" error ... to fix mysql.so error 

1)  edit the sources list:
	$  sudo gedit etc/apt/sources.list
2)  uncomment 
	deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
	deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
3)  update something (i don't know what this does but it worked :)
	$  sudo apt-get update
4)  get phpmyadmin package
	$  sudo apt-get install phpmyadmin
	(from [this post](http://www.ubuntuforums.org/showpost.php?p=124619&postcount=10) 
	note: to restart apache manually /etc/init.d/apache2 restart

now you should be able to get somewhere with
[http://localhost/mediawiki/index.php](http://localhost/mediawiki/index.php)

to move the config file
$  cd /
$  cd var
$  cd www
$  cd mediawiki
$  sudo mv config/LocalSettings.php LocalSettings.php

This is also up [on my blog AiEtc](http://aietc.blogspot.com/2005/04/installing-mediawiki-on-ubuntu-linux.html)

---

