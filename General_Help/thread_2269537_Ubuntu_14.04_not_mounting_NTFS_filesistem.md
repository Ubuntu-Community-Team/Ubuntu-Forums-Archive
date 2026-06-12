---
title: "Ubuntu 14.04 not mounting NTFS filesistem"
date: 2015-03-16
forum: General Help
---

### Post by echosmart on 2015-03-16
Hi
My Ubuntu 14.04 not mount NTFS filesistem, but after instalation mount corectly this filesystem

[https://youtu.be/2Lp2KG9H6Ao](https://youtu.be/2Lp2KG9H6Ao)

I-ts possible to solve this problem whitout new OS instalation ?

---

### Post by coffeecat on 2015-03-16
The error message is telling you what might be wrong. It is not a problem in Ubuntu.

Most likely problems: the RAKTAR filesystem is unclean and needs to be repaired in Windows. Or - when you last used Windows, you suspended the OS rather than shutting down and there is metadata in the filesystem which is preventing Ubuntu from mounting it.

Two questions: what is the RAKTAR partition and what version of Windows are you using?

---

### Post by echosmart on 2015-03-16
RAKTAR partition i-ts only for data, not booable filesistem partition.
I-m restart in Windows and close windows, but in linux apear same error.

Windows version user 8.1.

---

### Post by coffeecat on 2015-03-16
> **echosmart said:**
> Windows version user 8.1.

The problem is with Windows. Windows 8 defaults to so-called fast boot which means that it is merely suspended, not properly shut down. And this inevitably leads to the problem you are seeing in Ubuntu. You need to disable fast boot to ensure that Windows 8 shuts down properly.

I'll see if I can find a link for disabling fast boot.

---

### Post by coffeecat on 2015-03-16
This one is as good as any:

[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

You need option 1, and then at step 5 skip to step 7.

---

### Post by echosmart on 2015-03-16
Thanks for fast ansvers !
I-m reboot in windows and try to disable fastboot.

---

### Post by echosmart on 2015-03-16
Thanks again !
i-m disable fast booting in Win8.1, and now the filesystem was mounting succesfully !

All the best !

---

### Post by coffeecat on 2015-03-16
One thing to remember: if you do a restart in Windows back into Windows, you may see this same problem again. It's best to shut down from Windows each time. I had a brief pang of anxiety after Windows 8.1 prompted me to do a restart after an update. When I next booted into Ubuntu, I saw a similar error message to what you saw when I tried to mount my shared data partition. It was cured by booting into Windows and then doing a proper shutdown, of course, but it was still worrying for a few moments!

Good luck!

---

### Post by Mark Phelps on 2015-03-16
> if you do a restart in Windows back into Windows, you may see this same problem again. 

Quite true!! Because ... Windows ignores the setting for FastStartup when you select Restart, and thus, forces you into hibernation, even though that was most likely, NOT what you intended.  When you do ShutDown, Windows uses the setting you have for FastStartup.

---

### Post by echosmart on 2015-03-17
Thanks for fast and precise ansvers !

Al the best ! Levy

---

