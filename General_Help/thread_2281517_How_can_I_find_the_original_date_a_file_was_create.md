---
title: "How can I find the original date a file was created?"
date: 2015-06-07
forum: General Help
---

### Post by dorlow on 2015-06-07
I'm working on organizing some digital home videos.  I used to be really good on staying on top of it.  I dump videos into a folder then I go through and look at the last modified date within a few weeks or months and then rename the files to have the date in the name.  I've gotten really lazy about it in recent years.  I've just been dumping videos in there.  But today I want to start organizing them and renaming them so the date is in the name to make it easier for my kids to watch on our Plex media server.  I'm noticing a ton of my home videos now have last accessed date of 6/7/15 and last modified date of 10/15/13.  Something reset the last modified date so now I'm not sure of the exact dates these videos were all created.  Is there any other creative ways to figure this out?  I'm running Ubuntu 15.04.  But the drive the pictures are on are on a network NAS formatted with NTFS.  I was reading another Linux doc, but they were referencing inodes, and obviously NTFS doesn't have inodes.

---

### Post by SeijiSensei on 2015-06-07
The "POSIX" standard for Unix-like file systems doesn't store a file creation date.  Have you tried looking at the NAS with Windows?  You might have better luck.

Here's a somewhat technical discussion of the issue when it comes to filesystems like ext4: [http://unix.stackexchange.com/questions/91197/how-to-find-creation-date-of-file](http://unix.stackexchange.com/questions/91197/how-to-find-creation-date-of-file)

---

