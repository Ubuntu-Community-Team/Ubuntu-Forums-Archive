---
title: "Folders missing after 2 from 4 RAID5 discs lost power"
date: 2017-12-01
forum: General Help
---

### Post by vlabra on 2017-12-01
Hello,

I have 4 disc in RAID5 (HW supported) and it happened that 2 of them  lost power (probably corrosion on power cable connector, may be  vibrations, it was running for a while)
I fixed that, booted, RAID works well however some folders are missing.  It seems that Ubuntu did not noticed that these 2 disc were disconnected  and messed something up.
I tried fsck, it found and fixed some issues, but folders are still  missing. During fsck I noticed that it was fixing also some duplicate  blocks of inodes related to files in one missing folder, however the  path was missing name of this folder but inode number. It looked like  <1234>/<5678>/SomeFolder/SomeFile.ext.

Can anyone help me? 

BR,
Vladimir

---

### Post by Kirk Schnable on 2017-12-04
Since this is a hardware RAID, Ubuntu has nothing to do with managing drive failures, that activity is carried out by your RAID controller.  Since you have RAID 5 which has the ability to recover from 1 failure, your RAID controller most likely assumed your array failed when two drives went down.

On most hardware RAID controllers I've used, the controller card will put the array into an "Impacted" state if this occurs.  It is sometimes possible to recover from this state in situations like yours where the drives have not really failed.

If you had noticed this earlier, it might have been possible to put the two drives back and possibly un-fail it through some actions on the RAID card.  But, now that things have been heavily modified (running FSCK on a failed RAID array is not advisable), the data is most likely irretrievable.

---

### Post by vlabra on 2017-12-04
> **Kirk Schnable said:**
> Since this is a hardware RAID, Ubuntu has nothing to do with managing drive failures, that activity is carried out by your RAID controller.  Since you have RAID 5 which has the ability to recover from 1 failure, your RAID controller most likely assumed your array failed when two drives went down.
Yes, RAID state is carried by HW controller, however Ubuntu should at least detect it and stop touching it.
> **Kirk Schnable said:**
> On most hardware RAID controllers I've used, the controller card will put the array into an "Impacted" state if this occurs.  It is sometimes possible to recover from this state in situations like yours where the drives have not really failed.
Actually it did. RAID was shown with CORRUPTED state on boot screen. Ubuntu also see these 4 physical discs in addition to RAID, and here was also Unknown state.
> **Kirk Schnable said:**
> If you had noticed this earlier, it might have been possible to put the two drives back and possibly un-fail it through some actions on the RAID card.  But, now that things have been heavily modified (running FSCK on a failed RAID array is not advisable), the data is most likely irretrievable.
It was first and only time I noticed. I did not run FSCK on failed RAID, I ran it after I fixed it. The data were probably corrupted after failure before reboot, or may be after first boot after failure, because I found that it failed after boot. Ubuntu tried to mount the failed RAID and may mess it up here trying to do some recovery.

However, as I said, the files are somewhere in inodes structure, the problem is that parent folder(s) are not. So the question is how to bring them back

---

