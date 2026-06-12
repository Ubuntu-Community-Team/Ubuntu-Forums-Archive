---
title: "ATI 7730 and Ubuntu 12.10"
date: 2012-10-24
forum: General Help
---

### Post by Falc7 on 2012-10-24
I have installed kubuntu 12.10 on my new laptop, which has a Ati Radeon 7730.
I was following this guide to get the propritory graphics drivers working 
[http://wiki.cchtml.com/index.php/Ubu...e#Command_line](http://wiki.cchtml.com/index.php/Ubu...e#Command_line)

I did this:
sudo apt-get install fglrx fglrx-amdcccle
Then this:
sudo amdconfig --initial -f

However that seemed to brake everything, and I only got a command line interface on reboot.

So i reinstalled Kubuntu, and used the minimal config for the xorg.conf file
Section "Device"
Identifier "ATI radeon 7730"
Driver "fglrx"
EndSection

I tried forcing xorg to use the new xorg.conf file:
sudo amdconfig --input=/etc/X11/xorg.conf --tls=1

But it gave an error message

I decided to test whether the driver was working with
fglrxinfo

It isen't working. Not sure what else I can do, can anyone help?

Edit: One further question, If i mess everything up and get a command line interface again, is there a command I can use to delete the xorg.conf file, and avoid reinstalling everything again?

---

### Post by hal8000 on 2012-10-26
Similar problem here with an ATI5770 card and the fglrx driver on Ubuntu 12.10 (64bit)

First reboot the Unity login screen appeared, then just the wallpaper, no
menu bar and icons.


I used ctrl-alt-f2 broke into an alternate console and typed
lsmod

The fglrx module had not been created. I am using 64bit and will look into this. The kernel headers must be included and I did say one message from Synaptic that they had been removed.



Regarding your /etc/X11/xorg.conf   Its not really required as kernel mode settings are used instead.  Running aticonfig --initial will gnerate an xorf.conf which if present will be read, but should work without one.

Will post back when I have more info.

---

### Post by hal8000 on 2012-10-26
OK, I have got mine working and may have a solution for you.

First make sure you have kernel headers installed.

Then from synaptic install packages fglrx-updates  fglrx-amdcccle-updates

This will take a few minutes and kernel module fglrx should be built.
Reboot, I did not have to run

aticonfig --initial


and you should have an accelerated driver.
You can test from terminal with:

fgl_glxgears


I have a new problem now, not related to fglrx but using gnome-session-fallback, no titlebar appears on any open windows and I cannot move windows about.

Let me know if this solves your fglrx problem.

---

### Post by Falc7 on 2012-10-27
Nope didn't work :(

---

