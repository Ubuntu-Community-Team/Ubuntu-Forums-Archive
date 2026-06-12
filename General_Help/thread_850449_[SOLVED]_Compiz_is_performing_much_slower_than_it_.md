---
title: "[SOLVED] Compiz is performing much slower than it should"
date: 2008-07-05
forum: General Help
---

### Post by diablo75 on 2008-07-05
A friend of mine gave me his laptop to fix because he managed to break Compiz.  He did it by installing nvidia drivers when he doesn't even have an nvidia card.  Pulling those drivers got Compiz to run, but now it really seems to run poorly.  So poorly, you can see each frame being "painted" onto the screen at a framrate of about 3 a second.

HOWEVER!  The cube itself rotates perfectly smooth.... for some reason, it's the windows themselves that are performing slowing...

Anyone know what might cause this to happen?

---

### Post by psyopper on 2008-07-05
I would start looking at disabling plug-ins, particularly ones that render windows, especially Blur Windows. Also try running in GTK instead of Emerald to see if that helps. I'm guessing his video card doesn't support alpha blurring and these are the things you are trying to negate.

---

### Post by diablo75 on 2008-07-05
I don't really have any special effects like that enabled right now.  I even tried to open Appearence>Effects and then select Normal instead of Extra, but windows still seem to render very slowly.  For instance, when I have the CCSM open, and go to use the scroll wheel, it looks more like a remote desktop somewhere over the Internet, with how slow it takes to refresh the contents and the scroll bar to the screen.  That's about the best way I can describe it.  It just looks kind of like a VNC remote desktop session.

I recently installed the xserver-xgl package, which was not on the system originally.  I wonder what would happen if I removed it?  Because I don't think it was needed a long time ago in order to get compiz to run....

Edit:  THAT WAS THE PROBLEM ^^^

I installed the xserver-xgl package earlier in hopes of solving a separate problem (which was being caused by nvidia drivers that did not belong).

After removing that package, I now have very smooth performance!

---

### Post by isaacj87 on 2008-07-05
> **diablo75 said:**
> I don't really have any special effects like that enabled right now.  I even tried to open Appearence>Effects and then select Normal instead of Extra, but windows still seem to render very slowly.  For instance, when I have the CCSM open, and go to use the scroll wheel, it looks more like a remote desktop somewhere over the Internet, with how slow it takes to refresh the contents and the scroll bar to the screen.  That's about the best way I can describe it.  It just looks kind of like a VNC remote desktop session.

**I recently installed the xserver-xgl package**, which was not on the system originally.  I wonder what would happen if I removed it?  Because I don't think it was needed a long time ago in order to get compiz to run....

Whoa whoa, don't install XGL...Intel works out of the box with AIGLX. I bet if you remove it it'll help. I don't have it installed on my i915.

---

