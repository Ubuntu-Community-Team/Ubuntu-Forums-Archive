---
title: "Force the CPU to slow down"
date: 2013-04-22
forum: General Help
---

### Post by GameX2 on 2013-04-22
Hi,

I have this old game, Sonic R, which is kind of poorly programmed, for modern computer.  It wouldn't start if the CPU is too fast, and toss a random error, even with Wine.  The solution to make it start is to slow down the CPU, but I don't know how.

I managed to make it run in Wine, running a "useless" program a friend made: it allocate memory to the computer (Just for the fun of make it crash XD).  Running 3 of these "memory-eater" programs push my RAM to 90%, and the game start!

However, I'm not so used to do this - I hear the disk spinning, and eventually, that'll wear it out!

Any other solution?
Could I just run the program in a isolated area (Sandbox?) with only a limited RAM ammount ?  Like a virtual machine but.. without Windows?

I've succesfully started the game in a 512MB Windows 98 VM, but even 512MB was too much.  I started the program only once in the VM, and it has less impact on my system performance (It wear out the 512 MB of my VM, not my main computer with 8GB of RAM).  But running the program only once in that Windows 98 VM made the VM extremely sluggish, and the game unplayable (It started, at least).

Any easy solution, to slow down my CPU, or allocate only a small ammount of RAM to the game ?

Thanks!

---

### Post by mörgæs on 2013-04-22
[http://ubuntuforums.org/showthread.php?t=1777887](http://ubuntuforums.org/showthread.php?t=1777887)

I don't know how it works with Wine, though.

---

### Post by CatKiller on 2013-04-22
Using a [slowdown utility]("http://en.wikipedia.org/wiki/Slowdown_utility") would probably help. It's a known problem with older games and there are many solutions.

---

### Post by GameX2 on 2013-04-22
I've tried the few solutions I've found, including the package "cpulimit", but that didn't worked.
In the end, I've just found a unofficial patched version of the game, with the bug fixed.  It work perfectly:

[http://forum.cheatengine.org/viewtopic.php?t=418078&sid=1f17b176556655795a2b3c9156f869f3](http://forum.cheatengine.org/viewtopic.php?t=418078&sid=1f17b176556655795a2b3c9156f869f3)

Solved!

---

