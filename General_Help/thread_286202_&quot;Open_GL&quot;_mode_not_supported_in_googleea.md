---
title: "&quot;Open GL&quot; mode not supported in googleearth"
date: 2006-10-27
forum: General Help
---

### Post by leemckusic on 2006-10-27
:) 
Here is a fix to try if you see "OpenGL mode not supported" when trying to start googleearth. ( The Linux version of Google Earth viewer ),

edit the file /etc/X11/xorg.conf and change the DefaulDepth value:

like: 
sudo vi /etc/X11/xorg.conf

# Original was DefaultDepth     24
  DefaultDepth    16

Alternately you can change default depth using:

sudo dpkg-reconfigure xorg-xserver

------------------------------

The specifics of my experience are I am running a Matrox G400 video card.
Googleearth worked until I upgraded from Breezy Badger to 6.06 LTS.

I found this fix on the GoogleEarth community web site, Linux video problem area. The change is counter-intuitive, as other messages say "be sure to set 24 bit mode".

You must restart the xserver to see the change take effect. Restart computer is one easy way to do this.

-----------------------------

---

### Post by teich on 2007-05-30
Thanks.  This worked for me.  I'm running a Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller with the xserver-xorg-video-intel drivers on 2.6.20-16.  opengl was consistently crashing, but changing the bit depth has fixed this.  Everything looks pretty now...

---

### Post by tabris37 on 2008-01-11
im new to the terminal so I dont get how to edit my DefaultDepth from 24 to 16 once i open the configuration file please help

---

