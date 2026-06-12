---
title: "External hard drive problems..."
date: 2008-02-21
forum: General Help
---

### Post by Granddragon on 2008-02-21
So lately my external hard drive has been giving my some problems lately...
The drive works perfectly in linux i can read/write ect.
However, ever since i installed linux, the drive no longer works properly in windows

I can only see two folders "System volume information" and "RECYLCLER"

Any idea what would cause this problem? or how i can fix it?

the drive is NTFS btw.

---

### Post by Carl H on 2008-02-21
I have had a similar experience. Possibly the drive is slightly corrupted - Windows is having problems reading it, but Linux can cope with it no problem. 

The problem drive I had was "not a valid device" according to Windows, even though all my Linux machines could read it fine. 

You could try re-formatting it. If you're going to be using it with both Windows and Linux, then VFAT is possibly a better option than NTFS.

---

