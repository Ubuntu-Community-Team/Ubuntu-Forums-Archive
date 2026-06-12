---
title: "Loading external kernel modules"
date: 2007-01-30
forum: General Help
---

### Post by Rich78 on 2007-01-30
I was wondering if anyone could help?

I'm working on a project which involves the familiar kernel for use on an IPaq.  Although this is an Ubuntu forum I think the question I'm asking is more of a general Linux kernel question (and I do run Ubuntu on all my machines :D).

I've tried getting help from the familiar group but it seems like trying to get blood from a stone.

What I need to know is basically how I go about adding external modules to the familiar kernel?

To give you some background I recently installed what's known as the hh37 version of the Familiar kernel on my Ipaq.  It worked great with my wireless PCMCIA card but sadly wouldn't recognise my 4GB SD card.  I queried it with the familiar team and they offered me an unstable kernel known as hh42.

It installed no problem however it did come back with unresolved symbols.  At the time I didn't actually notice this (dumb I know).   However the SD card is now detected no problem, but then I discovered that the wireless PCMICIA card no longer works.  On further investigation it seems to be missing a driver which is actually one of the unresolved symbols.

Now I can get hold of the modules but the directory structure between the two kernels is different, in other words where the modules are located in hh37 is different in hh42 and often the directorys don't exist.  They're still in the lib/modules directory but the sub dirs are different.

Now I know how to insmod and depmod etc and locate the files relating to the unresolved symbols but what I need to know is does the directory structure matter?  and which structure do I follow hh37 or hh42.

If anyone could help I'd really appreciate it as I've really hit a brick wall on this one.

Thanks guys.

---

