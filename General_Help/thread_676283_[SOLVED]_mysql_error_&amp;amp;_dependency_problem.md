---
title: "[SOLVED] mysql error &amp;amp; dependency problem"
date: 2008-01-23
forum: General Help
---

### Post by cozmicharlie on 2008-01-23
When I run an update in Gutsy I get the following message:

E: mysql-server-5.0: subprocess post-installation script returned error exit status 1
E: mysql-server: dependency problems - leaving unconfigured

I have tried to reinstall mysql 5.0 but I just keep getting the same message.  ANy help would be greatly appreciated.

---

### Post by harlan on 2008-01-23
After

 $sudo apt-get install mysql-server-5.0

Try 

 $sudo apt-get -f install 

To solve the dependencies problems

---

### Post by cozmicharlie on 2008-01-24
Thank you for your help.  I did as you suggested and I get the following output.  I still get the same errors when I update.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server-5.0 is already the newest version.
mysql-server-5.0 set to manual installed.
The following packages were automatically installed and are no longer required:
  libgnucrypto-java libcairo-jni libdiscid0 libxmmsclient2 libxcb-xv0
  liblog4j1.2-java libswt3.2-gtk-java libseda-java libcommons-cli-java
  libgtk-jni blop libcairo-java libglib-jni libxcb1 python-qt3 ruby
  libcdio-cdda0 libbcprov-java libmikmod2 python-sip4 libxcb-shape0
  libsamplerate0 libglib-java libtunepimp5 libifp4 libgdk-pixbuf2
  libgtk1.2-dev libgtk-java python-elementtree libswt3.2-gtk-jni libxcb-shm0
  libid3-3.8.3c2a libxmmsclient-glib1 libofa0 libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up mysql-server-5.0 (5.0.45-1ubuntu3.1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
swoskow@stevegateway:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnucrypto-java libcairo-jni libdiscid0 libxmmsclient2 libxcb-xv0
  liblog4j1.2-java libswt3.2-gtk-java libseda-java libcommons-cli-java
  libgtk-jni blop libcairo-java libglib-jni libxcb1 python-qt3 ruby
  libcdio-cdda0 libbcprov-java libmikmod2 python-sip4 libxcb-shape0
  libsamplerate0 libglib-java libtunepimp5 libifp4 libgdk-pixbuf2
  libgtk1.2-dev libgtk-java python-elementtree libswt3.2-gtk-jni libxcb-shm0
  libid3-3.8.3c2a libxmmsclient-glib1 libofa0 libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up mysql-server-5.0 (5.0.45-1ubuntu3.1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by cozmicharlie on 2008-01-24
To anyone else having this problem - there is another thread ([http://ubuntuforums.org/showthread.php?t=665504&highlight=mysql](http://ubuntuforums.org/showthread.php?t=665504&highlight=mysql)) that addresses this same issue.  I will move my question to that thread so we do not have multiple threads dealing with the same issue.

---

### Post by cozmicharlie on 2008-01-29
For anyone with a similar problem what worked for me was to go to etc>mysql and open the my.cnf in a text editor.  Change the bind address to 127.0.0.1and save.  Worked for me.

---

### Post by Select* on 2008-03-09
This should fix your MYSQL installation / reinstallation issues, if your getting "dpkg: error processing mysql-server-5.0 (--configure):
" or other similar error.

If you have downloaded an already tried to install make sure all your mysql packages are removed. This step can be skipped, but I found when I had this issue I tried many different installation commands and wanted to remove all. The following command will remove MYSQL and MYSQL 5.0.

sudo apt-get autoremove --purge mysql-server mysql-server-5.0 
(^if root remove sudo)

Now reinstall with the following command, which will install the latest MYSQL

sudo apt-get install mysql-server 
(^if root remove sudo)

You will probably get the same error again, but don't dispair. Change to directory /etc/mysql/ and edit the my.cnf file by doing the following.

cp my.cnf my.cnf.bak
vi my.cnf

Once you have the file open navigate down till you see the bind-address setting. You may see two but only one should be un-commented. Change the bind-address setting so it looks like bind-address = 0.0.0.0 and save the file.

Now we will finish configuration of MYSQL by using the following command.

sudo dpkg --configure -a
(^if root remove sudo)

This command will continue all unfinished software auto configurations, in this case MYSQL. The database should start this time.

Edit the my.cnf file again to change the bind-address to the IP address of choice (127.0.0.0 for local only) or external interface IP address. Issue command to restart MYSQL and you should be good to go.

sudo /etc/init.d/mysql restart
(^if root remove sudo)

---

