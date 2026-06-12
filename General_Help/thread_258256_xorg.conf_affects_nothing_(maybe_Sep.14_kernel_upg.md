---
title: "xorg.conf affects nothing? (maybe Sep.14 kernel upgrade related?)"
date: 2006-09-15
forum: General Help
---

### Post by Sandlst on 2006-09-15
Ok, so I have had a quite.....interesting time getting this to work.  First of all, I upgraded it when it came out, and I had no problems the following morning.  In the afternoon however, un-happy things started happening.  The first thing was the X server not starting (I have an nvidia card) so I decided to edit /etc/X11/xorg.conf to use the 'nv' driver until I could get it working again.  After restarting gdm, I poked around for a little bit, reinstalled my kernel meta-package (linux-686) and nvidia-glx, changed the Driver option back to nvidia in my xorg.conf, and rebooted.  The first thing I noticed after booting was the fact that my fonts looked smaller (happens when I use the nv driver instead of nvidia) so at first I thought I had just skipped changing the drivers.  Opening my xorg.conf file, the drivers were set to nvidia.  After this I tried the command ```
glxgears
```which reported finding no glx extensions.  I then tried to run never winter nights, which failed to load because of the same problem.  I thought that maybe it was not reading the xorg.conf file for some reason, so I backed it up, then put random garbage in it to see if it would fail to load.  Restarting x worked fine, which worried me, so the next thing I tried was deleting the file all together.  Once again, X loaded just fine, so I tried to ```
sudo dpkg-reconfigure xserver-xorg
```Following the prompt I set up a new xorg.conf file, then tried to change the driver to nvidia, and restarted x.  After restarting X, the same problems from above happen.  Is there some way I could have possibly set the default xorg.conf file to something else, and if so is there a way to reset it?  Thanks in advance, sorry for the long read.

**UPDATE**
Getting desperate, I decided to try installing the nvidia driver using nvidia's installer; now all is working again, though I'm not sure how...

**UPDATE** Hmmm, the drivers loaded corectly only for that session.....but after turning my computer on, restarting gdm allows the drivers to load correctly.

---

