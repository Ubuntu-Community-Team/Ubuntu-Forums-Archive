---
title: "solved - high-res DVD problem"
date: 2008-01-30
forum: General Help
---

### Post by Big_Croc7 on 2008-01-30
Hi, I've just come across an interesting problem with my setup, which I've solved but thought I'd share the solution in case it can help anyone else.  I've got a new widescreen monitor (1680x1050 native resolution).  Plugged it in, switched on and ran 'sudo dpkg-reconfigure xserver-xorg' to set the new resolutions etc., fine, could then select 1680x1050 in system/admin/screen resolution.  However, after doing this, I coldn't play DVDs at all; Totem, Gxine and Mplayer all failed silently.  After a bit of playing around, it seems like the combination of graphics card and driver couldn't cope with playing DVDs at that resolution.  The solution was to install the restricted nvidia-glx drivers, and it now works fine (note: obviously, this will only help if, like me, you have an nvidia grahpics card, and were previously using other drivers).  If anyone else finds themselves in this situation it might be worth trying.

On a side note, should I report this as a bug somewhere? It would certainly have been easier to diagnose if their was some sort of error indicating the problem.

---

