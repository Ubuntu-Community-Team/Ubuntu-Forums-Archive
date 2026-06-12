---
title: "Services not starting on Gutsy (7.10)"
date: 2007-11-12
forum: General Help
---

### Post by brodiepearce on 2007-11-12
Hello all,

I did a fresh installation of Gutsy today, and have been having problems with the services.  When I boot into Ubuntu, none of the services seem to start;  I can't start Ubuntu normally because the loading screen and login screen still don't appear even after installing fglrx 8.42.3 using [this HowTo](http://ubuntuforums.org/showthread.php?t=591445) and doing a dpkg-reconfigure xserver-xorg with the usual settings I used for Feisty.

If start in Recovery Mode I can start GDM manually, and then login, however, once in, you soon discover that none of the services are running including dbus, so most of the Administration options can't be accessed.  If I start dbus manually, then I can access the Services dialogue, but it doesn't save my settings, I.e. I check the boxes of the services I want to start at boot, exit, and reopen the dialogue, and everything is blank again.

Please help if you can.  As you can understand this is particularly frustrating.  :(

---

### Post by taurus on 2007-11-12
When you reconfigure your X with "sudo dpkg-reconfigure xserver-xorg" command, make sure you pick **vesa** driver.

---

### Post by brodiepearce on 2007-11-12
> **taurus said:**
> When you reconfigure your X with "sudo dpkg-reconfigure xserver-xorg" command, make sure you pick **vesa** driver.

Why is that?  The vesa driver performs poorly compared to the newer fglrx drivers, and isn't it one of the causes of the infamous "Mesa issue" on ati cards...?

---

### Post by taurus on 2007-11-12
At least the vesa driver would let you get back into X again.  Then, you can install whatever driver you want after that.

---

### Post by brodiepearce on 2007-11-12
> **taurus said:**
> At least the vesa driver would let you get back into X again.  Then, you can install whatever driver you want after that.

I tried vesa just now, and also the fglrx driver in the Ubuntu repositories, and still get the same issue.  I can get into X fine with the 8.42.3 driver... the problem is that I have to start X/GDM manually.  Reinstalling a fresh copy now.

*edit*
The problem still exists after fresh installation... services-manager is still not saving my settings, GDM/X/dbus etc. not starting automatically.  This is just annoying now... I've never had any problems like this, it's always just been a matter of installing a video driver or something.

Another issue worth noting is that when I click on the Power button on the panel to restart or shut down etc., the display locks up (presumably due to some issue with GDM), and I'm forced to restart X to get any control back.

*edit*
Following 'advice' from a few people, I tried the LiveCD installer, and everything seems to be fine, no problems whatsoever, video was working out of the box, wireless also seems to be scanning properly with network-manager.  I can sort of understand the video working, but for the sake of closure I'd be interested if anyone knows why it has seemingly fixed my services problem.

---

