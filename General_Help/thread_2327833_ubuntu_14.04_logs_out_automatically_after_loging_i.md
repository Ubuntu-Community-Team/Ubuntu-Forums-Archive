---
title: "ubuntu 14.04 logs out automatically after loging in"
date: 2016-06-14
forum: General Help
---

### Post by babakflame on 2016-06-14
Dear Fellows
  
  I have no idea what has happened to my ubuntu 14.04. The only thing I can do is using a live ubuntu-14.04-amd64.iso file to have access to my files located in Trusty (ubuntu 14.04).

  Is there anyway that I can fix it or probably getting a backup and reinstall it from that backup to not lose my files?


  Regards

---

### Post by cariboo on 2016-06-15
A little better description of the problem might help. Are you in a login loop, where you login, and are taken tight back to the login prompt? Can you log into a console? Press Ctr-Alt=F1, and try to login at the ptompt

---

### Post by babakflame on 2016-06-15
I am using ubuntu 14.04 installed through a virtual box on an iMac. ctrl+alt+F1 did not work for me. However with ctrl+alt+F6 I have still access to the text mode of ubuntu. Whenever I log into the Ubuntu, it logs out automatically after couple of seconds. It seem that some processes are running in background. Recently, I deleted my sources.list and created another one through[https://repogen.simplylinux.ch/](https://repogen.simplylinux.ch/) website.
This is my current sources.list:
[HTML]#------------------------------------------------------------------------------##                            OFFICIAL UBUNTU REPOS                             #
#------------------------------------------------------------------------------#


###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ trusty main universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main universe 

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ trusty-security main universe 
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-security main universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main universe 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu trusty partner deb-src http://archive.canonical.com/ubuntu trusty partner[/HTML]


Can anybody help me please?

  Regards

---

