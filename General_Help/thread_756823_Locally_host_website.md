---
title: "Locally host website?"
date: 2008-04-16
forum: General Help
---

### Post by c-m on 2008-04-16
Hi,

I tend to end up playing with websites more and more and would like the ability to host them locally before uploading to the internet.

Is there a howto on setting up this functionality in Ubuntu?

Thanks

---

### Post by ruha on 2008-04-16
This is a good tutorial:
[http://howtoforge.com/ubuntu_lamp_for_newbies]("http://howtoforge.com/ubuntu_lamp_for_newbies")

put your website files in /var/www/ and open [http://localhost](http://localhost)

---

### Post by c-m on 2008-04-16
I set up according to that howto thanks.

Now how do I create a database, is there something like cpanal i use?

---

### Post by ruha on 2008-04-17
if you followed the tutorial, phpmyadmin should be installed in /www/phpmyadmin.
open [http://localhost/phpmyadmin](http://localhost/phpmyadmin) and you should be able to edit your databases.

---

### Post by c-m on 2008-04-17
I followed the tutorial to the letter. 

phpmyadmin is installed but certainly not in www/phpmyadmin

> carl@carl-desktop:~$ sudo apt-get install phpmyadmin[sudo] password for carl:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
phpmyadmin is already the newest version.
The following packages were automatically installed and are no longer required:
  libbcprov-java gnome-backgrounds nspluginwrapper esound
  libboost-date-time1.34.1 libglib-java libcommons-cli-java libgtk-jni
  libglitz-glx1 libglib-jni gnash-common libboost-thread1.34.1
  libgnucrypto-java libglitz1 libswt3.2-gtk-java libcairo-jni libcairo-java
  libgtk-java liblog4j1.2-java libswt3.2-gtk-jni libseda-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
carl@carl-desktop:~$ 


---

### Post by indytim on 2008-04-17
Poke around within your /var/www directory structure.  The folder for phpMyAdmin may be mixed case.

IndyTim

---

### Post by ruha on 2008-04-17
phpmyadmin could be installed in /usr/share/
copy the folder phpmyadmin to /var/www/ and it should work

---

