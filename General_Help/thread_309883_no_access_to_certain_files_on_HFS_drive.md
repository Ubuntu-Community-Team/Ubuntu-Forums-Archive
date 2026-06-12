---
title: "no access to certain files on HFS drive"
date: 2006-11-30
forum: General Help
---

### Post by phatzmb on 2006-11-30
I have a USB external hard drive that I was using with my macbook, which i (unwisely) formatting using HFS (or HFS+)
I copied over files from another ntfs hard disk.

Now that I connected the external hard drive to my Ubuntu machine, it was automatically mounted, but i can't access the files that were copied over from the old NTFS hard drive, however I can access any file that was since created on my macbook.

I assume this has something to do with file permissions? the problem is the macbook is under repair, so i can't change them in OS X. Is there a way of correcting this in Ubuntu?

---

### Post by mayonaise15 on 2006-11-30
Yeah, it does sound like a permissions error.  Can you give us an ls -l from one of the problem directories?  Honestly, I don't know anything about the HFS file system, but hopefully we can get the ball rolling on this.

---

