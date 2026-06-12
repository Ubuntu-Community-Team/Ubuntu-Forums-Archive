---
title: "[SOLVED] File system wrecked while partitioning"
date: 2008-03-17
forum: General Help
---

### Post by Diabolis on 2008-03-17
I was resizing one of my partitions with gparted through a live cd. Since that takes some time, I left my laptop alone for a while and when I came back all I saw was a black screen. I though at first that the black screen appeared due to the power saving feature, I moved the mouse several times and awaited to see if I could get the gui back. After an hour of continuously moving the mouse, I gave up and rebooted my pc.

I opened gparted again, and the partition has been successfully resized, it also says that the partition is almost full. The problem is that when I opened it, I could not see any of my files.

Now my question is, would **fsck** fix this? or do I have other options besides losing my files?

---

### Post by bodhi.zazen on 2008-03-17
You can try it ...

You may be able to recover some data with photorec :

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Or by un-doing the resize ...

---

### Post by Diabolis on 2008-03-19
I found out that the cause of the failure was some kind of bug in gparted that caused segmentation fault errors. I was using 0.2.5, so I upgraded to 0.3.5. After that I un-resized my partition and ran photorec. It recovered lots of files, but they are segmented in lots of pieces. How do I assemble them? photorec has some instructions for jpeg and image formats, but most of my files are mp3.

I don't really expect to recover my files, I already deleted de partition and made a new one. But I'll try anything just for the fun of it.

---

