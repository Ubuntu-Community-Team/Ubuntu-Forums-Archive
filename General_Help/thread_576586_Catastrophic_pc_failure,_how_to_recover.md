---
title: "Catastrophic pc failure, how to recover?"
date: 2007-10-15
forum: General Help
---

### Post by fishexe on 2007-10-15
My laptop is a dual-boot running ubuntu and windows.  Ubuntu has worked fine for 7 months but this morning I shut down using 'sudo shutdown -h now' and when I tried to boot about 30 min. later I saw the following:

[    66.790398] EXT3 -fs error (device hda5) ext3_fat_entry: reading directory #2796193 offset 1
repeated several times with different numbers and then
[   66.790647] Kernel panic - not syncing: Attempted to kill init!

I don't have any idea how to fix this.  Is this something I could fix by booting from CD and running fsck?  Will it cause any problems because it's ext3 and not ext2?  I have never run fsck on an ext3 fs before, is there anything I need to know?  Also, if my filesystem is irreparably damaged is there any way to get my data off?  The last time I backed up was months ago.

Thank you very much for any help you can provide me.

---

### Post by Pumalite on 2007-10-15
You can save data with Live CD:
[http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters](http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters)
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by fishexe on 2007-10-15
Update: Filesystem is clean

I booted from the Ubuntu install cd and ran fsck.  It said my fs was clean.  It still won't boot so I tried using Super Grub Disk ([http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/))
I'm going to have to lose some of my files, but that's ok because they're just mp3s I don't need.  I backed up the important stuff so I'm probably just going to reformat and reinstall.  I can't for the life of me figure out what the problem is since it's not in my fs and it's not in grub.

Thanks a lot for your help.

---

### Post by Pumalite on 2007-10-15
You are welcome.

---

