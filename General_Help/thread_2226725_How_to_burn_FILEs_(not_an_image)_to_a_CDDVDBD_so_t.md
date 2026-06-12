---
title: "How to burn FILEs (not an image) to a CD/DVD/BD so they can be read back by dd."
date: 2014-05-28
forum: General Help
---

### Post by nstgc379 on 2014-05-28
For reasons that are probably completely stupid, but at the moment seem pretty good, I want to be able to write a fixed number of files (5 at the moment) of equal fixed size (5GB) onto a BD-R and then read them back with something like dd. Ultimately this is intended to replace my current archiving scheme.

I'm currently starting off with CD-RWs, and have burned with wodim, a ~400MB to the disk. According to the terminal output it was successful, and the disk, on inspection of the medium, does appear to have been written to properly. When I tried "dd if=/dev/sr0 of=test" a file of 2kB, a single sector of the disk, was written. This I overcame with ddrescue, however I don't think that I can use it for multiple files.

[edit]The fact that dd doesn't work isn't really much of an issue since this is meant to be used with degraded optical media anyway. If the disk is bad, dd won't work anyway.[/edit]

Any suggestions?

---

### Post by anaconda on 2014-05-28
I think you have to give the bs (blocksize) to dd as an argument. Like this: (CD sectors are 2048 bytes, so this copies sector for sector.)
> dd if=/dev/sr0 of=/home/yourusername/mycd.iso bs=2048 conv=notrunc

---

### Post by nstgc379 on 2014-05-28
You're probably right, however it doesn't matter too much since ultimately, if I put this to use, I'll be wanting to use ddrescue, or something like it anyway, since dd isn't adequate for copying data off of degraded media.

[edit] Currently the issue is that I don't know how to do this with multiple files. With dd I have a general idea as to how I could output each to its own file. However I neither know how to write multiple files nor read them with ddrescue.

---

