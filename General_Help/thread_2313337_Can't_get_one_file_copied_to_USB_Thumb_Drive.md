---
title: "Can't get one file copied to USB Thumb Drive"
date: 2016-02-11
forum: General Help
---

### Post by tinman2 on 2016-02-11
I have a strange problems I've never encountered, using Ubuntu 14.04 LTS. I copied a bunch of .mp3's from my SSD to my thumb drive to listen to in my car, all of them copied just fine with the exception of one that refuses to copy using Krusader. It comes up with a box saying "could not write to /media/[drive name]/[song name]". The drive isn't anywhere near being full, and the .mp3 has the same permissions as the other .mp3's, and isn't corrupted. I can copy the .mp3 to my other drives, including another USB drive, but it refuses to go to my USB thumb drive.

Any idea's?

---

### Post by sudodus on 2016-02-11
The problem could be the combination of file name and file system (that the file name is not allowed in the thumbdrive's file system).

It could also be a problem with permissions.

(It could also be a problem with the file size, but I guess the size is smaller than 4 GB.)

What is the file name? Are there any spaces or special characters (other than letters a-z, digits 0-9)?

What is the file system in the thumb drive?

Which tool did you use to copy the files (the file browser Nautilus or some other tool)?

---

### Post by tinman2 on 2016-02-11
I never realized there could be a file name not allowed on a thumbdrive.  And as I stated before, it has the same permissions as the other files, and I was using Krusader.  Right after I posted this I used Nautilus and it copied just fine, so I have no idea as to why Krusader wouldn't do it...

---

### Post by sudodus on 2016-02-12
I still guess the reason is the file name. It could be how Krusader is managing/interpreting the file name; problems with some character in the file name.

If you want to find out, please tell us the file name :-)

---

