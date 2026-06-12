---
title: "Buggy Ezoom and desktop cube"
date: 2008-06-29
forum: General Help
---

### Post by phillymatt on 2008-06-29
Absolute beginner here: just installed Ubuntu Hardy Heron a few hours ago, and have zero previous experience with any form of Linux.

Fist thing I wanted to do was get Compiz Fusion up and running to see the eye candy so highly touted. Stumbled my way through intallation, and got the CompizConfig Settings Manager up.

Some things work (paint fire, rain, magnifier, benchmark, amongst them), but the two I care most about (desktop cube and enhanced zoom desktop) are buggy. 

With Ezoom, only part of the screen zooms in, a large portion of it (the majority of the screen, located in the top left quadrant) stays locked in place).

The desktop cube sort of flip, is choppy, broken, and uneven. 

I don't get it, and after trying to figure this out for three hours I'm begging to rethink my change in OS.

---

### Post by Eion on 2008-06-30
I'll do my best to help you with your cube problems, however I can't immediately come up with any answer to your zoom plug in problem.

Could you take a screenshot of your cube? (Applications>Accessories>Take Screenshot) And post it here?

---

### Post by phillymatt on 2008-06-30
To take a screenshot, I'm hitting super+button1 (left click). However, when I do so, it's taking them at 13x2 pixels (98 Bytes). I found that if I highlight a large section of the desktop (click and drag) it will then take a larger screenshot. 

However, the only way that I'm able to activate the "cube" is when I drag a window out of the desktop, and this makes highlighting disappear. So I can't take a screenshot.

If it helps, it doesn't look like a cube, it's scrambled, 2 dimensional, and with broken lines.

---

### Post by Eion on 2008-06-30
If you use the app that I suggested you can tell it to take after a delay. :)  Is your desktop size set to 4? CCSM>General>Desktop Size>Horizontal Desktop Size>4

---

### Post by Kenza on 2008-06-30
If you right click on the desktop icons in the bottom right tray you can adjust the columns and rows also, make sure columns are at 4 and the row is at 1. Otherwise, it really sounds like just a configuration issue...but i'm a n00b too =)

Edit: Another thing i thought of, where i messed up too before i installed Compiz, is to make sure you have the drivers installed for your video card i.e. System > Administration > Hardware Drivers

---

### Post by Eion on 2008-06-30
Kenza's right, you might have to enable restricted drivers.  If you keep having troubles you might consider registering at [http://forum.compiz-fusion.org/](http://forum.compiz-fusion.org/)

---

### Post by psyopper on 2008-06-30
> **phillymatt said:**
> To take a screenshot, I'm hitting super+button1 (left click). However, when I do so, it's taking them at 13x2 pixels (98 Bytes). I found that if I highlight a large section of the desktop (click and drag) it will then take a larger screenshot. 

However, the only way that I'm able to activate the "cube" is when I drag a window out of the desktop, and this makes highlighting disappear. So I can't take a screenshot.

If it helps, it doesn't look like a cube, it's scrambled, 2 dimensional, and with broken lines.

That is how the Screenshot Plugin works. It allows you to actively select the area you want to screenshot. To use the screenshot feature you press and hold the Super key and then drag a square around what you want to capture. If the cube is rotating then this obviously will not work. You can still use the Gnome Screenshot function by pressing the PrtScn key on your keyboard to get the whole desktop at once.

Are you using the CompizConfig Settings Manager? If so, go into the Rotate Cube plugin, Bindings tab, Rotate Cube section and set the "initiate" option to a button click. I recommend Alt+Button2. Then, while the cube is turning, take a screenshot with the PrtScn key.

If you are not using CompizConfig Settings Manager (CCSM), you should be. To install it open Synaptic Package Manager and install it from there.

To set up the desktop cube (you must have CCSM installed to do this properly) follow these directions:

[http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074)

You are complaining about video corruption. It would help us all to know what kind of video card you have and how you installed the drivers for it. Please share this information with us so we can help you to help yourself.

---

### Post by Eion on 2008-07-01
phillymatt did you get your problem resolved?

---

