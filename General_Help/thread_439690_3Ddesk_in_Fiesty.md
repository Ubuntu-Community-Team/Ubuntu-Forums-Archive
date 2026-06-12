---
title: "3Ddesk in Fiesty"
date: 2007-05-10
forum: General Help
---

### Post by bks on 2007-05-10
I recently upgraded to 7.04 from 6.10 and reinstalled the 3ddesk package with Synaptic.  When I try to run it or configure it I get an error saying:

bradford@bradford-laptop:~$ 3ddeskd
Daemon started.  Run 3ddesk to activate.
bradford@bradford-laptop:~$ 3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.

bradford@bradford-laptop:~$ locate 3ddesk
bradford@bradford-laptop:~$ find 3ddesk
find: 3ddesk: No such file or directory
bradford@bradford-laptop:~$ 

What do I do?

---

### Post by bks on 2007-05-10
I tried uninstalling, restarting and reinstalling...still no dice.

---

### Post by Nythain on 2007-05-11
dri isnt enable, or your video card drivers arent installed/correct...
do you have a nvidia/ati/intel video card???
output of glxinfo | grep rendering ???
contents of your /etc/X11/xorg.conf ???

---

### Post by bks on 2007-05-11
I do have an ATI card. I'll post the outputs when I get home.

---

### Post by bks on 2007-05-12
Here are the outputs you suggested.  I noticed that the xorg.conf lists my ATI Radeon Mobility 9000 card, but grep rendering = No.  ????  What next?

---

### Post by bks on 2007-05-12
The other strange thing is that I am able to play 3D games no problem, such as Chromium BSD and  gl-117 (which is an OpenGL game?!).

---

### Post by wyth on 2007-05-14
Are you using the proprietary drivers?

Two things:

A.) You could/should add this at the bottom of your xorg.conf file, because composite is enabled by default, and the ATI drivers can't do it.:
```
Section Extensions
     Composite    "Disable"
EndSection
```B.) Know that ATI 9000 basically isn't really well-supported anymore.  7.04 uses Xorg 7.2 and that won't play well with this relatively older card, fglrx isn't supporting ATI 9000, and the open source drivers really don't hold up to the ATI drivers.  

It's a sad state of affairs for us on ATI 9000.  I had to go back to Edgy.  ATI is being beligerant about the whole thing, so the only real hope is that the open source drivers somehow take a quantum leap in quality, but quantum leaps don't deem to happen easily in software development.

---

