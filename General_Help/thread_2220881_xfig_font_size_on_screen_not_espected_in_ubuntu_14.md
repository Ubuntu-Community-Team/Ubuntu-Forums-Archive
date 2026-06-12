---
title: "xfig font size on screen not espected in ubuntu 14.04"
date: 2014-04-29
forum: General Help
---

### Post by mazzanti on 2014-04-29
Dear all,

I've recently installed ubuntu 14.04 and xfig,a tool I use quite a lot to make document drawings.
The fact is that in this new ubuntu I've found that text on screen does not conform to the font size as it used to do
in every oher version I've used (I mean to say, same xfig version, different ubuntu release).
So no matter what foint size I set in xfig, the text I type becomes tiny on the screen, but once exported to 
.eps or .pdf, the resulting plot does really conform to the desired size. This is really a pain in a delicate place
since I can't really place text easily: I have to place it, export to .pdf, see the result, move the text a bit and iterate
this process all over again until I get the text in the right position -something I never had to do before because
the text was seen on the right scale.

As i don't seem to find anybody else experiencing the same issue, I guess it can be that I'm missing some fonts or
something else I don't know. So can anybody help me here? Do you know what fonts should I install to have xfig
working properly? Or is it really I bug?

Best regards and thanks,

Ferran.

---

### Post by jeffrey5 on 2014-04-29
Seems to be related to something I saw in my laptop in 12.04 (but not my desktop then). Once I installed gsfonts-x11, logged out and logged in, the problem is solved. (It may have been xfonts-x11 or gsfonts-other or something else if gsfonts-x11 doesn't work).

sudo apt-get install gsfonts-x11

---

