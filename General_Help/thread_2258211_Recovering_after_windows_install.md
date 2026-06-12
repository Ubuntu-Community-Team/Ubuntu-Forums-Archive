---
title: "Recovering after windows install"
date: 2014-12-25
forum: General Help
---

### Post by lachim-buzok on 2014-12-25
Hey guys!

I have this problem with my ubuntu 14.04, namely after a fresh windows 7 installation on one of my drives the usual happened, i.e. windows screwed up the boot sector so I had to use boot-repair (perhaps this would be helpful [http://paste.ubuntu.com/9591846/](http://paste.ubuntu.com/9591846/)) to get ubuntu back to load. However, after the repair everything stopped working: the interface rolled back to unity (i think - never really used it) - previously I had ubuntu-gnome installed and there also where no users to log on to except for the guest user. So after a few google look-ups I managed to restore my user and get a hold off the files I had in my home folder thanks to this guide [http://askubuntu.com/questions/279294/how-to-recover-root-user](http://askubuntu.com/questions/279294/how-to-recover-root-user) . But unfortunately the interface is still unity and all the installed programs seemed to have disappeared after I log on to my proper user (stuff like latex, gnuplot, blender - it's like they never existed on the machine prior to the boot incident). Anyone got a clue how to fix this - if at all possible?

Thanks in advance,
drink

---

### Post by yancek on 2014-12-25
Is your problem that you can no longer find specific programs such as the ones you mention?
Are you able to boot Ubuntu?
Are you able to boot windows?
How long have you had Ubuntu dual-booting with windows?  Is this a new install or have you been using Ubuntu for some time?
Had you previously set up gnome and now it is Unity?
I'm not sure I understand the problem and don't see how making changes to the bootloader would have this effect.

---

### Post by lachim-buzok on 2014-12-25
> **yancek said:**
> Is your problem that you can no longer find specific programs such as the ones you mention?
Indeed - anything that was previously installed seems to be gone now.
> **yancek said:**
> 
Are you able to boot Ubuntu?
Are you able to boot windows?

Double-check.
> **yancek said:**
> 
How long have you had Ubuntu dual-booting with windows?  Is this a new install or have you been using Ubuntu for some time?
Had you previously set up gnome and now it is Unity?

Two years or more. Decided to get myself another HDD and install Win7 on it. Previous setup had ubuntu-gnome and winxp working fine.
> **yancek said:**
> 
I'm not sure I understand the problem and don't see how making changes to the bootloader would have this effect.
Well I had to run boot-repair from a ubuntu live usb-stick - I imagine that could have screwed things the way they are now by making a new installation - but if that was the case I couldn't get my home folder back, could I? I guess it's something else - it just seems everything has been wiped except my home folder. Could it be that I didn't completely revert user privileges to the way things were before and that's causing this mischief? At this point I can't even select the type of session at login (previously it was gnome, gnome-classic and unity). I wonder if this can be fixed?

---

