---
title: "gksudo fade not recovering"
date: 2008-04-23
forum: General Help
---

### Post by hollymcr on 2008-04-23
I have upgraded to 8.04 beta.

Whenever an application requires root privileges, gksudo fires up the password dialog and fades out the rest of the screen. 

After I enter my password, everything works fine but the fade does not get "lifted" until areas of the screen get refreshed (eg by dragging windows around).

I think this is probably a driver issue (I'm using an Nvidia GeForce 6200 card, nvidia-glx-new driver), it wasn't a problem pre-8.04 and is not a problem on another PC I have which is also 8.04/Nvidia (but completely different hardware).

I note that my xorg.conf did not change at all during the upgrade, but I assume I have a newer nvidia driver now.

---

### Post by hackle577 on 2008-04-25
I think I'm having a similar problem. My screen will sometimes fade out randomly. I can get it back to normal easily, by moving a window or some such, but it's still an odd problem.

This doesn't occur when I use gksudo to do something though, just seemingly at random. :-\

I have an nVidia GeForce 7300GS (nvidia-glx-new driver) that doesn't have any other problems as far as I can tell.

---

### Post by charonn0 on 2008-05-08
I seem to be having the same (or similar) problem.

For me it almost always happens the first time in a session that I'm prompted for my password (i.e. if X gets restarted of I log out an in again, it will happen) but almost never after.

Also, the effect seems to be confined to the Gnome Panel. Once that part of the screen is updated (like by switching workspaces) everything is fine.

I'm using an ATI Radeon x300 with the fglrx driver and Ubuntu 8.04 (not a beta version, clean install of the final version)

Here's an example of what it looks like for me:
[IMG]http://i51.photobucket.com/albums/f351/charonn0/GUIError.png[/IMG]

---

### Post by 0x656b694d on 2008-05-08
Hi,

The same issue with my Ubuntu. Rotating the cube or calling the wall refreshes the picture and than everything is okay.

Somebody please submit a bug!

(nvidia-glx on GeForce4Ti, Hardy with all updates.)

---

### Post by charonn0 on 2008-05-08
> **0x656b694d said:**
> 

Somebody please submit a bug!



What should it be filed under? Compiz-Fusion, Gnome, ???

---

### Post by EnlistedSquire on 2008-07-06
+1 for this problem. Basically my entire desktop stays faded until I either drag a window over part of it to clear it or move the desktop cube to clear the whole lot in one go. I have Ubuntu 8.04 with an Nvidia 7800 GTX with EnvyNG (which I assume has installed the latest driver).

Did anyone find a solution or submit a bug?

[EDIT]I should probably mention I'm using dual-monitors, it may be relevant.

---

### Post by psyopper on 2008-07-06
+1

I thought I was the only one... Only happens with gksudo prompt for me, and seeingly randomly. Nvidia 6200 256 meg AGP 8x. Using the nvidia-glx-new package from the Hardy repos.

---

### Post by blueorder on 2008-08-01
Here too...

I have the same issue.

Hardy + Geforce FX 5600 Ultra + nvidia-glx-new

---

### Post by EnlistedSquire on 2008-08-02
Just posted a bug on launchpad:
[URL="https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/254218"]
https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/254218[/URL]

---

### Post by EnlistedSquire on 2008-09-13
Looks like a fix for this problem was released today (turns out to be a Compiz bug). I'll be interested to see if this problem is fixed for everyone.

---

