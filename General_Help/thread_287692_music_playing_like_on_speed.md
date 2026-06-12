---
title: "music playing like on speed"
date: 2006-10-29
forum: General Help
---

### Post by DougieFresh4U on 2006-10-29
[FONT="Comic Sans MS"]can some one please explain why music in all my music players ( amarok, Listen, rhythimbox) play like they all took 'speed'? I have recently started using Iceweasel & FlashPlayer 9 Beta?[/FONT] -**-SOLVED**

---

### Post by theslut on 2006-10-29
does your sound card have mutlirate locking enabled in the alsa mixer? sounds to me like it's stuck on a sample rate that's too low and it causes the music to play back too fast.

---

### Post by DougieFresh4U on 2006-10-29
I do not know anything about that. Maybe you could inform me how to check that. I do know that every thing worked ok, until a few days ago when I installed Flash Beta 9 in Iceweasel.

---

### Post by yabbadabbadont on 2006-10-29
I'm using Dapper and I discovered (by accident) that I'm getting the same behavior.  I determined that, at least on my system, it was only gstreamer based players that have the problem. Xmms and Xine both work correctly.  (which are the programs I normally use)  Which gstreamer plugins do you have installed?  You might try removing all of them and see if the problem goes away.  If so, add the plugins back one at a time until the problem returns.  Then file a bug.  (You might search launchpad for this problem first.)

---

### Post by DougieFresh4U on 2006-10-29
This problem only showed up **AFTER** installing Iceweasel & Flash 9 Beta plugin. Music played fine before.

---

