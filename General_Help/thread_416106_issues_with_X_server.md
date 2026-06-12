---
title: "issues with X server"
date: 2007-04-20
forum: General Help
---

### Post by nerdman978 on 2007-04-20
Ok I recently updated to Feisty Fawn and had the urge to finally get Beryl. So, I started to follow this howto:
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")
and started to fix the xorg.conf file how it says to. But, after restarting my computer, I get a screen telling me that X server cannot be loaded. I have no idea what I did wrong. I copied the type exactly as it says. So, I am stuck (and am lucky I have another computer). I have an ATI Mobility Radeon 9000 if that helps.

---

### Post by ronocdh on 2007-04-20
> **nerdman978 said:**
> Ok I recently updated to Feisty Fawn and had the urge to finally get Beryl. So, I started to follow this howto:
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")
and started to fix the xorg.conf file how it says to. But, after restarting my computer, I get a screen telling me that X server cannot be loaded. I have no idea what I did wrong. I copied the type exactly as it says. So, I am stuck (and am lucky I have another computer). I have an ATI Mobility Radeon 9000 if that helps.
I've been going through the same laborious process. I've had to rerun **sudo dpkg-reconfigure xserver-xorg** multiple times. Also, on several occasions I had to retype the commands **sudo aticonfig --initial** and **sudo aticonfig --overlay-type=Xv**.

I have not been able to get 3D acceleration on my tower (Radeon 9200SE 128MB) but I do have it on my laptop (Radeon X1600 128MB). However, my laptop Feisty install won't open the Desktop Effects preference pane (says "The composite extension is not available") while my tower can; only the tower can't do anything with it, of course! Oy vay.

---

### Post by nerdman978 on 2007-04-20
Ok so does anyone have a better howto to get Beryl?

---

### Post by jiminycricket on 2007-04-20
With your card it's difficult because you can only use XGL (not a Beryl problem though), thanks to ATI and I don't think the open source drivers support your card.  Anyways:

[http://ubuntuforums.org/showthread.php?p=2326330](http://ubuntuforums.org/showthread.php?p=2326330)
[http://ubuntuforums.org/showthread.php?t=291464](http://ubuntuforums.org/showthread.php?t=291464)

---

### Post by nerdman978 on 2007-04-20
WHAT THE HELL!!!! I tried using a few more of those tutorials/howtos and got the same error screen. But instead of being able to use the ```
sudo dpkg-reconfigure xserver.xorg
``` I get a lovely "- is not installed" message.

---

### Post by jiminycricket on 2007-04-20
Are you sure you typed:

sudo dpkg-reconfigure xserver-xorg , no period.

---

### Post by nerdman978 on 2007-04-20
Wow. Stupid mistakes like this.....
Anyway I decided to follow this howto:
[http://ubuntuforums.org/showthread.php?t=291464]("http://ubuntuforums.org/showthread.php?t=291464")

---

