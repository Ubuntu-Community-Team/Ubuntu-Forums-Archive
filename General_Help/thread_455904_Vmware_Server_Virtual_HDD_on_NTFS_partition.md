---
title: "Vmware Server Virtual HDD on NTFS partition"
date: 2007-05-27
forum: General Help
---

### Post by kalpik on 2007-05-27
Hi!

I have a peculiar problem.. If i place my virtual hard disk on an NTFS partition (im using ntfs-3g), then Vmware Server does not boot from it.. It works fine if i place it on my / partition (which is XFS). Though virtualbox is able to boot from virtual hard disks placed on NTFS partitions too. Anything that can be done?

Thanks.

---

### Post by cpmiller2 on 2007-06-25
I am experiencing a similar problem.  Initially I thought my Vmware Server install wasn't working properly and wasted some time messing with that.  I have a dual booting machine and a 500GB secondary drive that I would like to store all my VM's on so whether I'm booted in XP or Ubuntu I can run them.  Since i can only partition FAT32 to 196GB this problem is really causing me grief.  Any help or thoughts would be much appreciated.

---

### Post by cpmiller2 on 2007-06-27
I decided to reformat my drive and use ex3 to store my VM images.  When you boot in windows you can just use Ext2 IFS ([http://www.fs-driver.org/](http://www.fs-driver.org/)) to use the ext3 partitions.

---

### Post by kalpik on 2007-11-07
Sorry for bumping such an old thread, but i found the solution at: [http://www.ntfs-3g.org/support.html#vmware](http://www.ntfs-3g.org/support.html#vmware)

---

