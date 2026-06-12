---
title: "Updating and refreshing fstab"
date: 2007-04-06
forum: General Help
---

### Post by Kamco on 2007-04-06
I installed 64-bit Feisty on a computer that already had 64 and 32 bit Windows XP. This machine has four separate hard drives with a total of nine different partitions, mostly ntfs. My triple boot worked fine and I was able to mount and read all partitions from within Feisty. Using a drive imaging program I was able to move the Feisty installation to a different computer that also has two Windows installs, four separate hard drives, and several different partitions. Feisty seems to run fine in its new location except for one thing - the mounting of the  partitions is erratic. Apparently the fstab file now has several erroneous entries and the permissions on the mounted volumes seem inconsistent.

Is there a way for me to refresh and repair the fstab file so that it reflects the partitions now on this computer instead of the jumble of good and bad entries I have now? Can I do this without having to do a complete reinstall? Thanks.

Ken

---

### Post by benerivo on 2007-04-06
There is no automatic refresh/repair so you will need to edit it manually to delete the superflous entries. I would run nautilus in root mode and open the fstab file from there to edit it, but i believe the orthodox method is...
[http://www.ubuntux.org/mounting-hda1](http://www.ubuntux.org/mounting-hda1)

---

### Post by kidders on 2007-04-06
> **benerivo said:**
> There is no automatic refresh/repair so you will need to edit it manually to delete the superflous entries.That's correct. **/etc/fstab** is ... well ... the bible. Linux will do its best to obey, no matter how inconsistent its contents may be with your actual system. This behaviour is quite deliberate, so you need to be extremely careful when modifying this file.

> Can I do this without having to do a complete reinstall?It's worth pointing out that there are _absolutely no circumstances_ in which a problem with /etc/fstab would require a reinstallation. If you make a mess bad enough to prevent your system booting successfully (which is the worst-case scenario), any Linux boot CD and a few quick commands are all you need.

The next time you have nothing to do, performing the rescue procedure is worth practising. That way, if something bad ever *does* happen, you know you can fix it. :-)

---

