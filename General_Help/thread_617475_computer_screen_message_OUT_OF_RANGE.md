---
title: "computer screen message OUT OF RANGE"
date: 2007-11-19
forum: General Help
---

### Post by jasper-two on 2007-11-19
Hi 
New to Linux and just loaded ubuntu 7.10

After loading the restricted drivers for the graphic card Geforce 8500GT

and rebooted my computer screen comes up with a message OUT OF RANGE
Going in to dpkg-reconfigure xserver-xorg

I get a text message And have no ide what to do caN ANY BODY HELP I AM IN THE **** 
WITH THIS ONE

---

### Post by louieb on 2007-11-19
Wild guess. The out of range is referring to your vertical or horizontal refresh rate. If you have your monitors manual see what max is. 
boot in recovery mode   and run ```
dpkg-reconfigure xserver-xorg
``` Just accept the defaults until it comes to your monotor and select resolutions with refresh rates under the monitors max or 60kHz if you don't have the manual. When done reboot and see what happens.
Good luck

---

### Post by ryke on 2007-11-19
Hi,

This message is probably referred to your monitor.

In the file /etc/X11/xorg.conf you should look for this section:

Section "Monitor"
	Identifier	"Monitor genérico"
	Vendorname	"Dell"
	Modelname	"Dell E196FP"
	Horizsync	31.0-83.0
	Vertrefresh	56.0-76.0

Yu have to know the values ofHorizsync and  Vertrefresh for your monitor and change them.

To do that you have 2 options:

- As you said, run dpkg-reconfigure xserver-xorg and set the new values, or just

- Modify the file from the Terminal with the new values--> sudo /etc/X11/xorg.conf

Regards

---

### Post by jasper-two on 2007-11-19
Thanks for reply but I have a problem 

xxxxx@xxxxx-desktop:~$ sudo /etc/X11/xrg.conf
sudo: /etc/X11/xrg.conf: command not found
xxxxx@xxxxx-desktop:~$ sudo /etc/X11/xorg.conf
sudo: /etc/X11/xorg.conf: command not found
xxxxx@xxxxx-desktop:~$ 


So what can I do now

---

### Post by heathen on 2007-11-19
/etc/X11/xorg.conf is a file, not a command..

if you are trying to edit it "sudo nano /etc/X11/xorg.conf"

---

### Post by ryke on 2007-11-19
Hi jasper-two... I'm sorry... as heathen has said, I missed to write the program name (in that case, nano, a text editor).

sudo is just to act as root.... you should use it before the command (or program) that you want to use

sorry for the inconveniences

---

