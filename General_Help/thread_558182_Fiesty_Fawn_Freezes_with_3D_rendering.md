---
title: "Fiesty Fawn Freezes with 3D rendering"
date: 2007-09-23
forum: General Help
---

### Post by kopolov on 2007-09-23
Hi,
I am a new user to ubuntu.

I have the following spec in my laptop:

LG model F1
cpu - intel coreduo
graphic - 
lspci | grep Display
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
256MB RAM for video card

2 GB RAM for machine

problem is - 
every 3D rendering application (glxgears, screensaver) cause feisty to completely freeze.
Numlock or Cupslock are not working, mouse not responding.

I went over dozens of posts in different forums. No one seems to have a solution.

more over, when I run glxgears the FPS is quite low for this machine (about 1200 FPS and only because I lowered the color depth to 16 instead of 24, It used to be 900 FPS with 24).

I installed the 915resolution and followed the instruction, but nothing changed.
If anyone has any idea, please help.

I have been going on about this for the past 2 weeks now.

Thank you.

---

### Post by p_quarles on 2007-09-23
I have pretty similar specs on my laptop (same CPU & GPU, less RAM), which works fine, so I'd bet it's not any kind of straightforward hardware/driver problem.

One thing I will say is that the 3D screensavers in Gnome are pretty buggy on Intel cards. Have you tried running a more stable 3D application? A lot of people use 3D games for testing this, so you might want to give OpenArena or Planet Penguin Racer a try.

---

### Post by kopolov on 2007-09-25
No need to look for 3D applications.
running "glxgears" also freezes the X completely.
How much Frame Per Second do you receive when you run glxgears (at what resolution and color depth)?

Thanks.

---

