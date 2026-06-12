---
title: "POP3/SMTP Server setup"
date: 2005-04-03
forum: General Help
---

### Post by tavella on 2005-04-03
I've tried reviewing documents and howto's on the net but I have been unable to sucessfully setup a POP3 and SMTP server and get them to work correctly. Can someone please point me in the correct direction?

Thanks in advance!

---

### Post by Gandalf on 2005-04-03
[QUOTE=tavella]I've tried reviewing documents and howto's on the net but I have been unable to sucessfully setup a POP3 and SMTP server and get them to work correctly. Can someone please point me in the correct direction?

Thanks in advance![/QUOTE]
 what is your purpose of installing pop3/smtp, are you installing web/mail server?

---

### Post by tavella on 2005-04-03
[QUOTE=Gandalf]what is your purpose of installing pop3/smtp, are you installing web/mail server?[/QUOTE]

Yes. I will also have a web server setup also. It's for personal use.

---

### Post by Gandalf on 2005-04-03
[QUOTE=tavella]Yes. I will also have a web server setup also. It's for personal use.[/QUOTE]
 then to make evrything easier, install VHCS2 ( [http://www.vhcs.net](http://www.vhcs.net) ) so everyhing will be done automatic, that's my point of vue

---

### Post by tavella on 2005-04-03
[QUOTE=Gandalf]then to make evrything easier, install VHCS2 ( [http://www.vhcs.net](http://www.vhcs.net) ) so everyhing will be done automatic, that's my point of vue[/QUOTE]
 This will work for just one domain?

---

### Post by Gandalf on 2005-04-03
[QUOTE=tavella]This will work for just one domain?[/QUOTE]
 well yeah for one or multiple domains of course it will
BTW i didn't tried VHCS on ubuntu yet, i installed it on debian sarge, if you want try it, i'll help during installtion, here's my script to install it on debian sarge

```

#VHCS installation script by wael_nasreddine (Gandalf) 
 
#making directories, apt-get the needed packages etc... 
 
mkdir /root/vhcs_tmp 
mkdir /root/vhcs_tmp/install 
cd /root/vhcs_tmp/install 
apt-get update 
apt-get upgrade -y 
apt-get remove  -y lpr nfs-common portmap pidentd pcmcia-cs pppoe pppoeconf ppp pppconfig 
update-inetd --remove daytime 
update-inetd --remove telnet 
update-inetd --remove time 
update-inetd --remove finger 
update-inetd --remove talk 
update-inetd --remove ntalk 
update-inetd --remove ftp 
update-inetd --remove discard 
 
apt-get install -y ssh postfix postfix-tls proftpd-mysql courier-authdaemon courier-base courier-imap courier-maildrop courier-pop libberkeleydb-perl libcrypt-blowfish-perl libcrypt-cbc-perl libcrypt-passwdmd5-perl libdate-calc-perl libdate-manip-perl libmime-base64-perl libdbd-mysql-perl libdbi-perl libio-stringy-perl libmail-sendmail-perl libmailtools-perl libmd5-perl libmime-perl libnet-dns-perl libnet-netmask-perl libnet-perl libnet-smtp-server-perl libperl5.8 libsnmp-session-perl libterm-readkey-perl libtimedate-perl perl perl-base perl-modules bind9 diff gzip iptables libmcrypt4 mysql-client mysql-common mysql-server patch php4 php4-mcrypt php4-mysql php4-pear procmail tar original-awk libterm-readpassword-perl libsasl2-modules libsasl2 sasl2-bin apache2 apache2-common apache2-mpm-prefork libapache2-mod-php4 bzip2 
 
 
#getting the current vhcs package change it if new version is available 
 
wget http://puzzle.dl.sourceforge.net/sourceforge/vhcs/vhcs2.4.tar.bz2 
 
#decompressing archive and installing it 
 
bunzip2 vhcs2.4.tar.bz2 
tar -xvvf vhcs2.4.tar 
cd ./vhcs-2.4 
make install 
cp -R /tmp/vhcs2/etc/* /etc 
cp -R /tmp/vhcs2/var/* /var 
cp -R /tmp/vhcs2/usr/* /usr 
 
 
#changing the mysql password ATTENTION: REPLACE $mysqlpass with you password including quotes like "password" 
 
mysqladmin -u root -p password "new password here" 
 
 
#reupdating the apt-get list/system 
 
apt-get update 
apt-get upgrade -y 
apt-get clean 
 
#now you have to make something manually, in case of the execuation of the next line failed, you have to do exactly as this topic says --> http://vhcs.net/vhcs/en/support/forum/viewtopic.php?t=1172&highlight=bug+discovered  
 
/var/www/vhcs2/engine/setup/vhcs2-setup 
 
#the below 4 line must be executed!!!! 
echo "extension=mcrypt.so" >> /etc/php4/apache2/php.ini 
echo "extension=mysql.so" >> /etc/php4/apache2/php.ini 
 
echo "Include /etc/apache2/sites-available/vhcs2.conf" >> /etc/apache2/httpd.conf 
/etc/init.d/apache2 restart 
 
#adding daemon to linux boot 
update-rc.d vhcs2_daemon defaults 
update-rc.d vhcs2_network defaults 

```

---

### Post by tavella on 2005-04-03
[QUOTE=Gandalf]well yeah for one or multiple domains of course it will[/QUOTE]
 Thanks for the info!

---

### Post by Gandalf on 2005-04-03
[QUOTE=tavella]Thanks for the info![/QUOTE]
 i edited the post above please review it

---

### Post by tavella on 2005-04-04
[QUOTE=Gandalf]i edited the post above please review it[/QUOTE]

Gandalf,

Thanks for all of your help again! Everything works beautifully except for one thing.... web pages... How do I set this thing up to allow my own custom webpages?

Thanks!

---

### Post by Gandalf on 2005-04-04
[QUOTE=tavella]Gandalf,

Thanks for all of your help again! Everything works beautifully except for one thing.... web pages... How do I set this thing up to allow my own custom webpages?

Thanks![/QUOTE]
 what do you mean by that? did you succeded to see VHCS2 setup page?

---

### Post by adamcs on 2005-08-06
Installing VHCS2.2 or VHCS2.4 on Ubuntu hoary(5.04) is easy, [COLOR=DarkRed]can also be used for upgrades from older versions and betas[/COLOR]

Type into the console the following commands :
```
wget http://www.siemens-mobiles.org/vhcs/vhcs.sh 
``` 

Then execute the script as a super-user with:
```
sudo sh vhcs.sh 
``` 

and follow the screen instructions!  It's that easy! \\:D/

---

### Post by andril on 2005-08-09
I am a noob - is this something that I can do with ease? Or should I leave it alone and let Win habdle the serving? Please help :)


OOOps! I guess I screwed up I got this error.

"mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: YES)'
ERROR # 1 : There was an error changing the password." can you help?

---

