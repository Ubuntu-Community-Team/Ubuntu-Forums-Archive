---
title: "Edgy is slow - help needed"
date: 2006-11-08
forum: General Help
---

### Post by Erik Trybom on 2006-11-08
I upgraded from Dapper to Edgy and it seems everything runs a lot slower now. Moving windows around and scrolling web pages is very sluggish. This happens in both Gnome and Xfce, so perhaps it has something to do with X itself? 

Trouble is I don't really know where to start troubleshooting. Is there anyone who knows what could be wrong?

---

### Post by SRParda on 2006-11-08
It is like the video driver is not configured properly.

**What video card are you using ? **

**What video drivers are loaded in /etc/X11/xorg.conf ?**

You can use [COLOR="RoyalBlue"]dpkg-reconfigure xserver-xorg[/COLOR] to reconfigure X.

---

### Post by Erik Trybom on 2006-11-08
I'm using an S3 ProSavage card, and the "savage" driver. It seems correct. 

Reconfiguring xorg didn't solve the problem either. I ran your command, went through the choices and restarted X, but things still run slow. The processor works pretty hard too.

Well, thanks for your advice anyway. I'll see if anyone else comes up with something or else reinstall the whole system.

Edit: Strange... I rebooted and now it seems to work like it used to. I thought restarting the X server would be enough.

Well, thanks anyway. The reconfigure thing seems to have done it after all.

---

### Post by procras on 2006-11-08
I had slowness issues with my network configuration.

Try and take down your network interfaces and see if this is the cause.

sudo ifconfig eth0 down

---

