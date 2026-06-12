---
title: "Problems with Blender in Edgy"
date: 2007-04-15
forum: General Help
---

### Post by nakedfanatic on 2007-04-15
Hi,

I have a problem when I render scenes in Ubuntu Edgy. Blender uses up all of the available RAM and then most of my 2gig swap partition before the desktop becomes completely unresponsive and I have to reboot. I have tried the repo Blender, The latest build on blender.org and an optimized build from blenderbuilds. I have also tried rendering in the background from the command line, but I still run in to the same problem. Only very simple scenes render OK.

I have no problems rendering under XP on the same machine.

The funny thing is that Blender's 3D modeling window runs about 10X smoother on Edgy.

Can someone please help me. I am new to Linux, but very keen to learn. I would like to think that my next computer won't need any Windows at all :D

---

### Post by nakedfanatic on 2007-04-17
An adequate solution to this problem was posted when I asked the same question on the blenderartists.org forum. The trick was to lower the "swappiness" parameter. Not sure how it works, but it works.

Please check out [this thread]("http://blenderartists.org/forum/showthread.php?p=854573#post854573") if you're interested in the details.

---

