---
title: "Desktop Effects could not be enabled"
date: 2008-05-25
forum: General Help
---

### Post by root_hacker on 2008-05-25
hi guyz

I have a ubuntu 8.04 live cd and i boot my acer 1642 laptop with it and enable desktop effects just with single click i liked the stuff pretty much so i installed ubuntu and formated my suse 10.2. Now after installing ubuntu in my hard disk i tried to enable desktop effects but it gives me an error desktop effects could not be enabled.

I have search forums and run some commands i am sending you output of those commands.

Compiz Check returns
----------------------------

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 


lspci | grep VGA

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)


compiz --replace ccp
Checking for Xgl: not present. 
No whitelisted driver found


I have also run this command to install xgl driver
sudo apt-get install xserver-xgl

But still no luck please help me out here really confused as desktop effects running fine with live cd but can't enabled after installing ubuntu.

---

### Post by overdrank on 2008-05-25
Hi and you may look at the sticky in this forums
[http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)

---

### Post by Forlong on 2008-05-25
[COLOR="Red"]**root_hacker, do not run the command from that link, it might crash your X-server when running Compiz next time!**[/COLOR]


Post the output of ```
grep -v ^# /etc/X11/xorg.conf
``` and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

