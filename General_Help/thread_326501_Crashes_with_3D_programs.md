---
title: "Crashes with 3D programs"
date: 2006-12-27
forum: General Help
---

### Post by JohnBortion on 2006-12-27
X keeps crashing when I run Armegatron, or the Darkplaces Quake 1 3D engine.  I'm using the default Xubuntu driver for my Ati 9800 pro, which is "ati".  It's probably a problem with DRM.  How can I find out what the problem is?  I looked through /var/log.  I'd really like to get darkplaces going under SDL.  It doesn't crash with GLX, but it's terribly slow.  Thanks.

---

### Post by kc8hr on 2006-12-27
Hi,

I doubt that the open-source ati driver is accelerated, which is what you need for the programs you mentioned.

I am not that familiar with ATI cards,  but you might check out their website for a proprietary accelerated driver.

Good Luck!
Tim

---

### Post by JohnBortion on 2006-12-27
Glxinfo says that 'direct rendering' is enabled.  I can see the game come up and run really great for a couple of seconds, but then it freezes.  If I compile with glx enabled, the game is sooooo slow.  I've never been able to get an open source 3d game to work on linux, but now that I'm close, I don't want to give up.  I'd rather use what's openly available driver-wise.  Thanks for the reply.  The other people that are running ubuntu right now are really great people.  It makes me want to help out other people with the little bit that I know.

The odd thing is how much faster the game runs (for a couple of seconds) before it freezes.  I know sdl is the right way to go.  I'm going to try it on a different computer and see what happens.  Thanks.

---

