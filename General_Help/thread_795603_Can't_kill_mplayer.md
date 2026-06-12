---
title: "Can't kill mplayer"
date: 2008-05-15
forum: General Help
---

### Post by lodp on 2008-05-15
Since upgrading to Hardy, it has occured to me a couple of times that I ended up with an mplayer or kmplayer process that ate up lots of CPU power and I wasn't able to kill. Neither by pid nor with killall.

If I enter "sudo killall -v mplayer", it says "Killed mplayer(15117) with signal 15", but the process lives on.

I've never seen a process I couldn't kill up till now --  not even restarting X does the job... There must be a way to do it without rebooting, right?

---

### Post by amorangi on 2008-05-16
I'm getting the same problem killing a totem - I've tried killall -9 totem and kill -9 3265 (the process ID), nothing will kill it. What other commands are available to end a process.  Totem is in status Uninteruptible, using 100% of a core for CPU time of 2d01h. I don't really want to have to reboot to get rid of it.

---

### Post by ironwolfe on 2008-05-16
you could try the gui kill

```
xkill
```

This will make an "x" mouse pointer - click on the window you want to kill

---

### Post by amorangi on 2008-05-16
The process doesn't have a window. It was only when I went into the System Monitor that I noticed this wayward process.

---

### Post by fsmithred on 2008-05-16
You could try 'pkill mplayer' but that probably won't be any better. If ps ax shows a Z or D with that process, you won't be able to kill it, but it might go away on its own after awhile.

If it's still running because it's sees an open file, you might try 'sudo lsof | grep mplayer' and find another process id to kill.

---

### Post by BlueSkyNIS on 2008-05-17
I have finished watching a movie and normally closed totem. After that CPU usage went to constant 50% (dual core CPU) and it seems I can't kill the totem process. I tried kill -9 17454 kill -KILL 17454, top kill with sign 9...nothing helps. System monitor is unable to kill it either, it says "Uninterruptible"?!

I'm using Hardy 8.04, with proposed updates enabled, nvidia drivers (8600gt) and v17-generic kernel.

EDIT: Forgot to mention: I was trying to kill it even as a root user.

Maybe, it's this bug: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/230993]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/230993")

---

### Post by amorangi on 2008-05-17
My totem was indeed in D status, and unkillable. It ran at 100% of one of my cores till I rebooted. Surely there must be another way to kill a process other than those outlined above.

---

### Post by red_yanagi on 2009-03-08
I had exactly same problem with this.
I could fix this problem as below.

I could kill it by xkill if it has a window,
or I could kill it by System Monitor (System - Administration - System Monitor).

Hope this could be useful to you.

---

