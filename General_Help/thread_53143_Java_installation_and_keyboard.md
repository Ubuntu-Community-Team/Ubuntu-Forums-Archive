---
title: "Java installation and keyboard"
date: 2005-07-30
forum: General Help
---

### Post by emperon on 2005-07-30
Hello i am trying to install Java from this link
[https://wiki.ubuntu.com//Java15](https://wiki.ubuntu.com//Java15)

And when i type below i got the following error


onur@arrakis:~/Desktop$ sudo apt-get install java-package
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package


I am quite new to Ubuntu but i thought this command should run out of box but it doesn't. What should i do ?

Secondly i am changing my keyboard layout to Turkish from preferences menu in gnome but theres no apply option and keyboard layout doesnt change. 
How so ?

Onur

---

### Post by jasmuz on 2005-07-30
Do this:

1-Open a terminal

2-type sudo gedit /ect/apt/sources.list

add these lines to it:

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

Save and close,

3- type sudo apt-get update 

4-After that is done type sudo apt-get install sun-j2re1.5

And thats all!....afterwards you should have working java.

---

### Post by emperon on 2005-07-30
Thank you for the reply.
I forgot to mention. The thing i was trying to install is JDK not JRE.
So how your solution matters on this basis ?

2ndly currently it is chosen as Turkish Alt Q keyboard layout in the preferences. Although i have rebooted the computer. It is still in english when i type (while turkish setting is preserved)

---

