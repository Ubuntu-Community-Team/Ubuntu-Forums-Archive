---
title: "Horrible system crash with some applications"
date: 2015-02-03
forum: General Help
---

### Post by buntuyu on 2015-02-03
After upgrading to 14.04.1 LTS, i began to experience a supernasty system crash when launching certain apps, like blender and vlc. I get a black screen and a blinking cursor, no command-line input.

I don't remember anything similar in my years with Ubuntu.  It may involve some type of (gradual but quick) memory flooding, because, in some episodes of this crash I was first able to shell out to a console screen, and log in, with very slow response, and then quickly the system would become impossibly slow, and then completely non-responsive, requiring a brute-force power-down.

Where do I begin to diagnose this?  I realize I might need, at some point, to turn to the help groups for the particular apps, but i'd like to know what I can do beforehand, to maximally observe and identify the problem, using the system.

  I've searched online, at length, for postings about a similar problem, but no one seems to have instant and complete crashing, upon launch of the application.  I launch blender, and before anything from blender is drawn on the screen,  I get the black screen.  Blender is locally built; vlc is app-get-gotten.  I've been updating my 14.04.1 system.

Thanks in advance.

---

### Post by mooreted on 2015-02-03
What video card do you have and what driver is currently installed? Maybe the video driver is causing problems due to the update.

Did you check dmesg, .xsession-errors, and system logs?

Open a terminal and run top, then open Blender is see if it looks like a major memory leak.

That's all I can think of off the top of my head.

---

