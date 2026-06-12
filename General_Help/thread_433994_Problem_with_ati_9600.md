---
title: "Problem with ati 9600"
date: 2007-05-05
forum: General Help
---

### Post by Medion on 2007-05-05
I am trying to get desktop effects work with my Dell Inspiron with ati 9600. The easy way of  automatically activating driver + effects in the gnome meny didn't work.

The change I've done to the system is getting the right resolution by typing
sudo dpkg-reconfigure -phigh xserver-xorg
and changing my keyboard to norwegian in xorg.conf

I then tried to follow this guide:
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

I copied and pasted from firefox to gedit, to make the changes to the xorg.conf file. 

When I got to the part where I should restart x, it wouldnt restart, and I got an errormessage. I restarted ubuntu, but X wouldn't start. I's possible to log in without x, but not for long, because that error message pops up all the time. The errormessage is "[1263.108000]bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed". 

What can I to to fix this problem?

---

### Post by Medion on 2007-05-06
Or if there is some kind of "default" basic xorg-file, I can log in in recovery mode an rewrite it. I can also change the file back by following the guide i reverse, but I dont know how to reinstall the driver then. Anyone know how to help?

---

