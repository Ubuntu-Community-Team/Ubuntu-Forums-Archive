---
title: "How do I switch between an AIGLX-session and a normal GNOME-session?"
date: 2006-07-21
forum: General Help
---

### Post by Sethiano on 2006-07-21
Hi all!

I've finaly got AIGLX working after many, many atempts with both XGL and AIGLX.

Now, allthough AIGLX+Compiz looks awesome, I would not like to have it as my standard session. So the solution would be to make two diffrent GDM sessions, like [this guide]("http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29") describes for XGL.

I tried to come up with a solution that would work with AIGLX, but failed.

As you can see in [this guide]("http://www.ubuntuforums.org/showthread.php?t=145068&highlight=AIglx") that I followed, one have to do changes in the /etc/X11/xorg.conf file.
If you restore all the changes in the Xorg.conf and also in the /etc/gdm/gdm.conf-custom as described in the AIGLX-guide, GNOME will start with a with a normal Xorg server and compiz and AIGLX will not be loaded.
So if it would be possible to have two copies of the Xorg.conf and load the corresponding file when you choose your session then this should work. Is this possible? 

So I guess one have to code some kind of script or something, but this is unfortunely out of my current ubuntu skills :( .


If there anybody besides me that have/had this problem and maybe got a solution, don't hesitate to answer this thread!

Many Thanks!

---

