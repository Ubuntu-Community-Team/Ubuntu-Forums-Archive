---
title: "Unable to locate package phpmyadmin (Ubuntu server 14.04)"
date: 2014-05-27
forum: General Help
---

### Post by Cole189 on 2014-05-27
Hello, I am new to the Ubuntu community and setting up what you may call a personal cloud server using, Samba, Apache, mysql, and php.
While attempting to install the package phpmyadmin i get the error,
[FONT=courier new]
apt-get install phpmyadmin[/FONT]
[FONT=courier new]Reading package lists... Done[/FONT]
[FONT=courier new]Building dependency tree[/FONT]
[FONT=courier new]Reading state information... Done[/FONT]
[FONT=courier new]E: Unable to locate package phpmyadmin[/FONT]

My sources.list file looks like this,

[FONT=courier new]#############################################################[/FONT]
[FONT=courier new]################### OFFICIAL UBUNTU REPOS ###################[/FONT]
[FONT=courier new]#############################################################[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]###### Ubuntu Main Repos[/FONT]
[FONT=courier new]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main universe[/FONT]
[FONT=courier new]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main universe[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]###### Ubuntu Update Repos[/FONT]
[FONT=courier new]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security main universe[/FONT]
[FONT=courier new]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main universe[/FONT]
[FONT=courier new]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-proposed main universe[/FONT]
[FONT=courier new]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security main universe[/FONT]
[FONT=courier new]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main universe[/FONT]
[FONT=courier new]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-proposed main universe[/FONT]



I thank you for your time and help.

---

### Post by sameermw on 2014-05-28
Did you run ```
[COLOR=#111111][FONT=monospace]sudo apt-get update[/FONT][/COLOR]
``` first and then try to install phpmyadmin ```
[COLOR=#111111][FONT=monospace]sudo apt-get install phpmyadmin[/FONT][/COLOR]
```. try this it worked for me.

---

### Post by Cole189 on 2014-05-28
> **sameermw said:**
> Did you run ```
[COLOR=#111111][FONT=monospace]sudo apt-get update[/FONT][/COLOR]
``` first and then try to install phpmyadmin ```
[COLOR=#111111][FONT=monospace]sudo apt-get install phpmyadmin[/FONT][/COLOR]
```. try this it worked for me.

Thanks so much can't believe I didn't try this haha thanks so much for your time.

---

### Post by brian_milnes on 2014-11-19
This process didn't work for me...:mad:

---

### Post by slickymaster on 2014-11-19
> **brian_milnes said:**
> This process didn't work for me...:mad:

Please don't hijack other people's threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

