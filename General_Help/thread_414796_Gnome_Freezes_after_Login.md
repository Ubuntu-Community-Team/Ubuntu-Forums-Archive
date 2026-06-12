---
title: "Gnome Freezes after Login"
date: 2007-04-20
forum: General Help
---

### Post by EtniesBMX on 2007-04-20
I have u/x/kubuntu feisty installed. When I choose gnome and login, the computer hangs up and a white box about 1/4 the screen appears in the upper left corner. I then hit CTRL+ALT+Backspace and log in to Kubuntu. I notice many instances of **xrdb <defunct>**  running in the background.

I have reinstalled ubuntu-desktop, but with the same results.

I am using a GEForce FX5200 card.

The xsession-error file was so big that it had to be broken into two files to be uploaded. Also uploaded is my /etc/X11/xorg.conf  file. 

Thanks in advance!

---

### Post by EtniesBMX on 2007-04-21
In case anyone has a similar problem, I fixed this one by renaming/deleting the file **.gconf** in my home folder and restarting the computer.

---

### Post by TimDuncan on 2007-04-23
Hey, i have this same problem after upgrading to feisty..

Deleting the .gconf only fixes it for the first login. Once you press ctl alt backspace and logout, the same problem happens again.. Any help please!??!! im desperate.. I've looked everywhere.

Any reply would be greatly appreciated

Tim

---

### Post by EtniesBMX on 2007-04-23
I had that same problem. I fixed it by renaming the .gconf file, logging in to Gnome and not messing around with anything and then restarting the computer (rather than just restarting the x server).  

This problem is really frustrating. I hope that works for you!

---

