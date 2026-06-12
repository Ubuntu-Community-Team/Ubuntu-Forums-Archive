---
title: "[SOLVED] Blender crashing"
date: 2008-01-24
forum: General Help
---

### Post by Boguz on 2008-01-24
Hey

i just installed blender 2.44

i was following a tutorial about making text and stuff.
everything went ok until i tried to render it.
as soon as i click in the render button it all crashes.

i ran it from the console and i got this:

> Compiled with Python version 2.5.1.
Checking for installed Python... got it!
*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 471
Software fallback:ctx->Line.SmoothFlag
***************************************************************************
*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 470
Software fallback:ctx->Line.StippleFlag
***************************************************************************
*********************************WARN_ONCE*********************************
File r300_mem.c function r300_mem_alloc line 225
Ran out of GART memory (for 1048576)!
Please consider adjusting GARTSize option.
***************************************************************************
Error: Could not get dma buffer... exiting

i am running blender on Ubuntu 7.10 and i have a ATI Radeon Mobility.
(hmmm, how can i check if i have the right codecs?)


(when i was using windows blender worked, so i think this is not because i am missing ram or something like this. i think i am missing something or i have something with a bad configuration on my linux)

Any ideas?

Thank you so much!

---

### Post by Boguz on 2008-01-24
i found [THIS]("http://forum.ubuntuusers.de/topic/137666/") page talking about the same problem, but it is in german and i cannot understand a thing...  lol

---

### Post by Boguz on 2008-01-24
i changed the APG settings in my bios from 64 to 256 and now it works...
:P

---

### Post by aBitLater on 2008-01-26
[QUOTE=Boguz]i found THIS page talking about the same problem, but it is in german and i cannot understand a thing... lol[/QUOTE]


search the german page address in google, then choose, "translate this page"

[http://translate.google.com/translate?hl=en&sl=de&u=http://forum.ubuntuusers.de/topic/137666/&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3Dhttp://forum.ubuntuusers.de/topic/137666/%26hl%3Den%26sa%3DG]("http://translate.google.com/translate?hl=en&sl=de&u=http://forum.ubuntuusers.de/topic/137666/&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3Dhttp://forum.ubuntuusers.de/topic/137666/%26hl%3Den%26sa%3DG")

---

