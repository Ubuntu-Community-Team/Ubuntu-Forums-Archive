---
title: "Slow remote VNC connection on Ubuntu"
date: 2019-02-05
forum: General Help
---

### Post by abhinavrawat on 2019-02-05
Hi 

I have intel NUC machine [https://www.amazon.in/Intel-NUC-Kit-NUC7i7BNHX1-Optane/dp/B071949CZP](https://www.amazon.in/Intel-NUC-Kit-NUC7i7BNHX1-Optane/dp/B071949CZP) on which I have installed Ubuntu 16.04. When connected via HDMI, it works perfectly fine. I have installed remote vnc on it so that I can access it from anywhere. This machine is installed at remote client location.
I can easily access the machine from vnc viewer from my office but the connection looks very slow. I have confirmed good internet speed at both ends so internet connection is not an issue. But still, the overall performance is very slow as it takes time to load any graphical thing like opening a browser or a file. 

Previously I installed windows 10 on the same Intel NUC and connected it through remote vnc, everything was working fine, so it looks like some issues with the ubuntu only as it work fine with windows.

Can anyone please suggest any setting which I can do increase the overall speed or any other alternative to this. I basically just need to access the terminal of ubuntu.

Thanks

---

### Post by HermanAB on 2019-02-05
Ayup - Ubuntu is not exactly a speed daemon.  If you want it faster, install xfce4.  Otherwise, use SSH, not VNC.

There are two reasons why modern Linux desktops are slooow:
a. Mandatory Access Control: SELinux or AppArmor.
b. Gnome DE

You can disable MAC, but that could make your system more vulnerable and you can replace Gnome with XFCE, LXDE or any other DE, but that may make it a little more clunky.

The fastest Linux system is probably Slackware and the fastest BSD system is probably OpenBSD, both of which don't use MAC and use a simpler GUI by default.

---

### Post by abhinavrawat on 2019-02-05
Hi HermanAB

You mentioned use SSH not VNC, but I am controlling the machine from remote, how to access ssh of ubuntu from remote.?

---

### Post by HermanAB on 2019-02-05
Enable the SSH Daemon:
[http://ubuntuhandbook.org/index.php/2016/04/enable-ssh-ubuntu-16-04-lts/](http://ubuntuhandbook.org/index.php/2016/04/enable-ssh-ubuntu-16-04-lts/)

and read the Snail Book:
[http://www.snailbook.com/](http://www.snailbook.com/)

---

### Post by abhinavrawat on 2019-02-05
I need to access it from remote and by remote I mean to say outside of client's network. Intel NUC Ubuntu is connected at clients network and I want to access it from my office

---

### Post by HermanAB on 2019-02-05
You need to forward the NUC SSH port to the outside on the client's router.  This should not be any different from what you do with VNC.

---

### Post by abhinavrawat on 2019-02-05
Anyways thanks for the xfce4 desktop environment, using this resolved the issue

---

### Post by HermanAB on 2019-02-05
When I need a fast system for engineering use, I usually install the Ubuntu Server version and then install XFCE on that to get a DE.  That ensures that I end up with a minimum of preinstalled cruft running on the machine and everything is then nice and snappy.

---

