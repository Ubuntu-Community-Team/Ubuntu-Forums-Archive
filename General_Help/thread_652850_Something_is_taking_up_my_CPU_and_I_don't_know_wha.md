---
title: "Something is taking up my CPU and I don't know what."
date: 2007-12-29
forum: General Help
---

### Post by Gigamo on 2007-12-29
This is a really weird problem.

My CPU is a Intel T7700. It has SpeedStep enabled so that it switches from 800, to 1200, to 1600 or to 2400MHz depending on what it needs to run.

Since last night, something is making it rampantly swap from 2401, back to 800, back to 2401, then to 1200, then back to 800, back to 2401, etc. All in a matter of like 10 seconds. 

See my screenshot. I should also mention that the gnome-system-monitor and Xorg in the system monitor are also switching cpu usage every second from what you see in the pic, back to 6%, then back to like 18%, back to 3%, etc, every second. Also, the abnormal CPU behavior is there when I close the gnome-system-monitor, while in the system monitor that is the one that appears to be the cause :?

---

### Post by TidusBlade on 2007-12-29
Maybe you ran a certain program and when you quit it, the system start slowing down? OR maybe a resource heavy graphics application, since Xorg is taking alot of CPU power...
Does it happen all the time? Try rebooting... Or maybe your accessing an external device to do something, whenever I use K3B to copy a CD, system slows down during the whole process.
On a side note, whats that applet or thing you use to generate stats at the right side of the screen?

---

### Post by bernied on 2007-12-29
Is it compiz causing the problem?
Have you tried turning off desktop effects?

---

### Post by Gigamo on 2007-12-29
> **TidusBlade said:**
> Maybe you ran a certain program and when you quit it, the system start slowing down? OR maybe a resource heavy graphics application, since Xorg is taking alot of CPU power...
Does it happen all the time? Try rebooting... Or maybe your accessing an external device to do something, whenever I use K3B to copy a CD, system slows down during the whole process.
On a side note, whats that applet or thing you use to generate stats at the right side of the screen?

That would be conky.

Anyways, I have not tried rebooting yet, but it's alot better in Fluxbox (I juts switched session to it). It still happens when firefox is loading new pages tho, this is what I just noticed.

---

### Post by Gigamo on 2007-12-29
I have discovered that this must be a firefox bug. I have added a line in conky to show highest CPU usage by percentage and by name, and everytime I load a new page in firefox firefox will jump to 20% for a second and then go back all the way to 0-1%. 

Is this a bug, is there a fix for it? Or am I stuck :D

---

