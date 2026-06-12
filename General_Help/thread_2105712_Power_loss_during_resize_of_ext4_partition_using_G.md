---
title: "Power loss during resize of ext4 partition using Gparted"
date: 2013-01-16
forum: General Help
---

### Post by Bliepo32 on 2013-01-16
Hey everyone,

I have a major problem. I was resizing (expanding + moving to the left) an ext4 partition on an external drive. During the resisze, I tripped over the power cable of my laptop and since the battery has been dead for quite some time, it lost power immediately. My question is: is there any way at all to recover the data and undo the damage?

---

### Post by haqking on 2013-01-16
> **Bliepo32 said:**
> Hey everyone,

I have a major problem. I was resizing (expanding + moving to the left) an ext4 partition on an external drive. During the resisze, I tripped over the power cable of my laptop and since the battery has been dead for quite some time, it lost power immediately. My question is: is there any way at all to recover the data and undo the damage?

Yes, you restore from the backup you made right before you decided to make major system changes ;-)

Peace

---

### Post by Bliepo32 on 2013-01-16
> **haqking said:**
> Yes, you restore from the backup you made right before you decided to make major system changes ;-)

Peace

Unfortunately, I didn't have the disk space to do so. I am guessing this simply means that there is no way to recover the data?

---

### Post by haqking on 2013-01-16
> **Bliepo32 said:**
> Unfortunately, I didn't have the disk space to do so. I am guessing this simply means that there is no way to recover the data?

you could try testdisk

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by oldfred on 2013-01-16
Part of data is in one place and part in another. And partition tables on file locations are not correct.

You may be able to use photorec to scan drive for anything that looks like a file. It takes a really long time and you do not get filenames, just extensions or file types. And you have to have another drive with enough room. 
I used it and it found every text file I had but found all the previous deleted copies & I was never sure I found the final saved version. A lot of file compares and searching. Weeks to resolve details. I now backup a lot more.

       Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

   Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by Bliepo32 on 2013-01-16
Thanks a lot. I will try using photorec. Hopefully it will be able to save my data.

---

### Post by haqking on 2013-01-16
> **Bliepo32 said:**
> Thanks a lot. I will try using photorec. Hopefully it will be able to save my data.

get yourself a external HDD for backups in the future. (it saves alot of headaches)

Peace

---

