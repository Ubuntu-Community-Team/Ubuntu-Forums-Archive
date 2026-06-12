---
title: "Installing Vtiger CRM on Edgy"
date: 2007-02-10
forum: General Help
---

### Post by ralanyo on 2007-02-10
I had a rough time getting this installed. The .bin install just doesn’t work. So I used the source installation method. Some of the stuff that I did in this example is a little unorthodox, but that is because I am fairly new to Linux and the shell commands. 

This worked for me when I couldn’t find a straight forward tutorial anywhere. I hope this helps.

I am using Ubuntu Edgy Eft- Even though I am somewhat new to Linux, I still refuse to use a gui with a server. There is only one way to learn and that is to dive right in. 

---The only thing that I haven’t gotten working yet is the imap piece------

1.	Install Ubuntu Server addition. [http://ubuntu.com](http://ubuntu.com) – in this example I used vmware to install Ubuntu and had XP as my host machine.

2.	Install SSH-Server so that you can remote to your server.(not necessary but I like to use Putty)

Sudo apt-get install ssh

3.	If you haven’t installed LAMP on your server during the installation then you must install them all separately. Use the commands below.

Sudo apt-get install Apache2
Sudo apt-get install Mysql-server
Sudo apt-get install  php5
sudo apt-get install php5-gd

restart apache

sudo /etc/init.d/apache2 restart

4.	Install mysql for apache http server

sudo apt-get install libapache2-mod-auth-mysql
sudo apt-get install php5-mysql

5.	So that you don’t have to keep typing sudo every time, login with as root.

su root

Then type your password.

6.	By default mysql doesn’t have a password set for it’s root account. It is a good idea to set this for security purposes.

a.	mysqladmin -u root password YourNewPasswordGoesHere
b.	restart mysql server
c.	/etc/init.d/mysql restart

7.	On a separate machine download the vtiger tar file. Extract it and burn the extracted “vtigercrm” file to a disc. |

8.	Put the disc into your ubuntu machine and mount it.

Cd /media
Mount /cdrom

9.	Go to the Cdrom directory

cd /cdrom

10.	 While still in the cdrom directory,  Copy the vtigercrm file to the default root directory of the apache server. (/var/www)

Cp –r vtigercrm /var/www

You will now have a vtigercrm file directory in your www directory.

11.	Open up a browser on another machine on the network to test the folder:

a.	[http://localhost/vtigercrm](http://localhost/vtigercrm)
b.	Or [http://ipaddressOfTheServer](http://ipaddressOfTheServer)

If everything copied over correctly you should have the configuration screen ready to set up vtiger.

12.	Go through the setup. You will notice that you don’t have write permissions set on any of the files. In order to set those permissions, I used:

Cd /var/www/vtigercrm
Chmod 777 filename    
 
	Ther is one that they don’t tell you about. It is the /var/www/vtigercrm/cache/ images file. Change the permission on this one too. If you do not, you won’t be able to see the dashboard images.

13.	You will know the file name because the configuration screen will tell you that the permission aren’t right. Once you set the proper permissions, refresh the page. All of them should turn green for ok.

14.	Click the next button and set up the data base. Put your username and password. Check the box to create a database, put the root password in and under hostname type: localhost.

15.	You should be set to go.

---

### Post by callump on 2008-06-25
I resolved the issue with IMAP support by adding the php-imap package:

  sudo apt-get install php5-imap

---

