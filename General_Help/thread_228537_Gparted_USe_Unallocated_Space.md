---
title: "Gparted USe Unallocated Space"
date: 2006-08-03
forum: General Help
---

### Post by OffHand on 2006-08-03
Hi
I wondered if it is possible to somehow expand one of my partitions with the unused space.
I have been decreasing the size of my swap partions and now I would like to use this freed space.
I have attached a ss of my partions in Gparted.
Thanks in advance.

---

### Post by OpsVentus on 2006-08-03
You can resize the partitions. I would like to advise you to use the GParted live cd. ([http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828))
You can resize /dev/sda5 or /dev/sda6 onto the first unallocated part.
And /dev/sda9 onto the second unallocated part.

Click on the partition to enlarge and click "resize/move", make it as big as possible.

Good luck,
Bart.

ps. resizing partitions is a dangerous task, backup is advised.

---

### Post by OffHand on 2006-08-03
> **OpsVentus said:**
> You can resize the partitions. I would like to advise you to use the GParted live cd. ([http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828))
You can resize /dev/sda5 or /dev/sda6 onto the first unallocated part.
And /dev/sda9 onto the second unallocated part.

Click on the partition to enlarge and click "resize/move", make it as big as possible.

Good luck,
Bart.

ps. resizing partitions is a dangerous task, backup is advised.

Thanks for your advice. Would be backing up to a different partition be good enough or can it screw up the disk as a whole?

---

### Post by OpsVentus on 2006-08-03
Should be sufficient, but there's always a change of corrupting the disk completely.
Depends on how important the data is to you.

Cheers,
Bart.

---

### Post by OffHand on 2006-08-03
I didn't have much luck with the live cd.
It booted quite fast but when Gparted was trying to find my partitions it didn't progress. When I quite Gparted and wanted to start it up again, it refused to do anything at all. Then I had to reset my computer because the reboot function stopped working  :S
I suppose I will wait for the next release.

---

### Post by OffHand on 2006-08-03
Ok,this is what I did. I made a back of my files on the last (FAT32) partition.
Then I deleted the partition and made a new partion using the unallocated space before the FAT32 partition too. 
Saved about 1.8GB of unused space  :)

---

### Post by OpsVentus on 2006-08-04
Yes that's the other option, safer aswell!

---

