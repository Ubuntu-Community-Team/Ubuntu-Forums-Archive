---
title: "Memory leak?"
date: 2006-12-01
forum: General Help
---

### Post by wgscott on 2006-12-01
I think I am having some sort of memory problem.  So is my computer.

I am running Xubuntu at the moment, but have gnome, kde, enlightment and probably 4 other desktop environments available.  I can reboot, and over the course of a couple of days without doing anything, I have this happen:

```
-% free -m
             total       used       free     shared    buffers     cached
Mem:          1010        995         15          0        530        273
-/+ buffers/cache:        191        819
Swap:         2047         17       2029

```

So almost 1 gig of memory is used, and the computer is essentially idle.  I can find nothing obvious when running top.


Where do I start to diagnose this and identify the culprit?

I started using Xubuntu (Xfce4) at the time I upgraded to edgy.  I have no idea whether that has anything to do with this or not.

I'm reasonably unix-literate but don't know much about memory issues.

---

### Post by RAOF on 2006-12-01
You'll notice
```
-/+ buffers/cache:        191        819
```

That means that 819Mb of your RAM is being used by the kernel as cache.  Don't worry about it.  The natural state of a Linux system is to be at 100% memory utilisation.

Should any program request more memory, the kernel will just give it some of that cache.

---

### Post by wgscott on 2006-12-01
Thanks.  For some reason on Mac OS X (which I am more familiar with) the division between active/inactive/free shows up differently.

Right now my iMac (running OS X) that has 1.5 GB of memory has 1.48 used (~0.8 of which is active and ~0.5 of which is inactive) and about 25 MB "free".

---

### Post by RAOF on 2006-12-01
Actually, it seems that according to [http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management) I've mis-interpreted your *free* output.  It seems that the buffers/cache line means that, as far as programs are concerned, you have 819 Mb of memory **free**.

---

