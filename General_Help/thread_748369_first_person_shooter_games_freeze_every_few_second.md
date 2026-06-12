---
title: "first person shooter games freeze every few seconds"
date: 2008-04-07
forum: General Help
---

### Post by Chryana on 2008-04-07
Hi. I have been running various versions of kubuntu since versions 5.xx . Right now, I'm running 7.10. The problem I have is the following. Whenever I try to play a first person shooter game, no matter what the game is, the screen will freeze every few seconds. The freeze itself isn't very long, but it makes it difficult to play any shooter games at all. I have tried the games quake 2, quake 3 and ut 2004, and they all display this behaviour. My computer isn't all that new, but it has a fairly decent video card, and all these games run smoothly under windows xp, so I'm not exactly sure of what the problem is. My system specs are as follows.

Athlon XP 2000+
1 G DDR RAM
500 G PATA hard drive
nvidia 8800 GS AGP

Any suggestion would be appreciated. Thank you.

---

### Post by SOULRiDER on 2008-04-07
This might not have anything to do, but just to discard a possible cause of the problem try disabling tracker and see if you still have that problem. Check this out:
[http://ubuntuforums.org/showthread.php?t=591867](http://ubuntuforums.org/showthread.php?t=591867)

---

### Post by Brebs on 2008-04-07
If you are [running this](http://www.nvnews.net/vbulletin/showthread.php?t=109478&page=2):
```
nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1
```
With nvidia driver 171.06, then I suggest trying:
```
nvidia-settings -a InitialPixmapPlacement=0 -a GlyphCache=1
```
Because the 2 made my nvidia 8800 pause for a half-second every few seconds, in opengl games.

---

### Post by Crafty Kisses on 2008-04-07
Is it possible you have Compiz running?

---

### Post by SOULRiDER on 2008-04-08
> **Codename said:**
> Is it possible you have Compiz running?

That should indeed make the games slower, but it will affect them all the time and not just sometimes.

---

