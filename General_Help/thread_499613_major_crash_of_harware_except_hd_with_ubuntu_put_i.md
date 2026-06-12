---
title: "major crash of harware except hd with ubuntu put in new box no boot"
date: 2007-07-12
forum: General Help
---

### Post by pparvin on 2007-07-12
I had to take a hd with ubuntu out of a box and put it into a dif box with diff video and even dif cpu (dual core to single core)  I can get to shell but don't know how to reload or whatever I need to do to get ubuntu to re-assess the video and cpu etc.  Any ideas would be appreciated... I have some stuff on the drive I would not like to loose !!

Thanks in advance:confused:

---

### Post by AdamG51172 on 2007-07-12
You should go with
> sudo dpkg-reconfigure phigh xserver-xorg

Then either reboot or start gdm from the prompt.

This will set the initial video options.  Since you have changed video cards, the xserver just needs to update the xorg.conf file.   

I don't believe that the CPU should have to be configured, unless you want to have some cpu scaling functionality.

---

### Post by pparvin on 2007-07-13
I tried this and got dpkg-reconfigure   command not found ..... I was logged in as root 
somthing else I am doing wrong ???

I used sudo and got package not installed phigh

---

### Post by pparvin on 2007-07-14
here is error screen

xwindow system version7.1.1
release 12 may 06
x protocol version 11 version 0 release 7.1.1
log    /var/log/xorg.0.log
config   /etc/x11/xorg.conf

I cannot get to x11 under etc says does not exist even though it shows in ls

can I just reinstall overtop ubuntu and not loose my files?

---

