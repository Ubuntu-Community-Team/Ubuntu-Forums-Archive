---
title: "Re-Image Windows Partition using ghost and grub"
date: 2007-05-17
forum: General Help
---

### Post by mwacky on 2007-05-17
I have an older pc setup with a dual boot between feisty and win2k, went through alot of trouble to get this setup.  Here is my question: If I re-image my win2k os using Norton Ghost, will that wipe away the grub making ubuntu inaccessible?   And if so how would I fix the grub?

Thanks!

---

### Post by IgnorantGuru on 2007-05-18
The older versions of ghost would not touch the MBR so I assume grub will not be affected.

Your can restore grub with 
```

grub-install /dev/hda   (or whatever device or partition)
```

or read this...
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

You can also backup your entire MBR or just the boot code in it as follows...
Backup:  dd if=/dev/hdx of=MBR-backup bs=512 count=1
Restore:  dd if=MBR-backup of=/dev/hdx bs=512 count=1
Backup Boot Code Only:  dd if=/dev/hdx of=MBR-backup bs=448 count=1
Restore Boot Code Only:  dd if=MBR-backup of=/dev/hdx bs=448 count=1

(replace hdx with the correct device... hda, etc)
(note that the entire MBR stores both the boot code as well as the partition table.  So if you change the partition table you should restore the boot code only!)

Should you need to restore it and you can't boot linux try a liveCD or [www.sysresccd.org](www.sysresccd.org) 's liveCD.

And in case you're interested, here is a linux version of ghost that I've had great results with...
[http://ubuntuforums.org/showthread.php?p=2148017#post2148017](http://ubuntuforums.org/showthread.php?p=2148017#post2148017)

---

### Post by mwacky on 2007-05-18
Thanks for your help!  I'll give it a shot and reply back with results.

---

