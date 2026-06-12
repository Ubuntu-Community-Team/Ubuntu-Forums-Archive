---
title: "X Server fails to start after installing some packages"
date: 2020-04-13
forum: General Help
---

### Post by detl_ on 2020-04-13
Hi,
I broke my X server somehome and cant get back to my last working version. (Although im not sure if this is caused the error)

I run ubuntu 20.04.

I tried to install 'gir1.2-gtop gir1.2-networkmanager-1.0 gir1.2-clutter-1.0' because I wanted to have the 'system-monitor' applet to work.

After reboot the X server fails to start. I can login to the command line.
The Xorg.0.log does only show 'Server terminated successfully (0). Closing log file.ializing kms color map for depth 24, 8 bcp.xinit: connection to X server lost)

I tried to reinstall xserver (apt-get install --reinstall xorg) => without success.
I removed .Xauthority => without success
I called 'Xorg -configure' => shows me an error 'Number of created screens does not match number of detected devices) [I have got an AMD 570 Mainboard with integrated Graphic card plus an additional graphic card]

I started from an Ubuntu bootable stick => X Server starts up perfectly.
I copied the xorg.conf.d directory from the boot device to my system => without success


Now I have no more ideas how to fix this error.
Can someone please tell me how to fix this error without installing ubuntu again ???

Thanks for your help.
Detlef

---

### Post by Claus7 on 2020-04-14
Hello,

just some idea: have you tried typing startx while at command line? You might see some errors that will guide you to the right direction.

Regards!

---

