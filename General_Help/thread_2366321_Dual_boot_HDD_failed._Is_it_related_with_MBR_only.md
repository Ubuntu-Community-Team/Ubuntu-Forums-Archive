---
title: "Dual boot HDD failed. Is it related with MBR only?"
date: 2017-07-16
forum: General Help
---

### Post by tozden on 2017-07-16
I have Ubuntu 14 & Win7 dual boot laptop with a grup loader default to Ubuntu.

Today I received a blue screen on Win7 and laptop couldn't boot after hard-reset. Bios recognizes the HDD but unable to load boot loader.

I have now booted via Ubuntu Live USB and try to check via boot-repair what might be the issue. I have read the output but couldn't figured out the problem:
[https://paste2.org/BeKE9GBh](https://paste2.org/BeKE9GBh)

Can you please advise me what I can do? At the moment I prefer to recover my original partitions but if it is impossible please advise me what to do in order to recover some important files in the both Ubuntu & Win partitions??

---

### Post by oldfred on 2017-07-16
Hard reset often corrupts data and then chkdsk if Windows or fsck if ext4 is required on your partitions.

But you are not showing any larger drive with any partitions.
Does BIOS show your hard drive? What size is hard drive?

If BIOS shows drive, in Gnome Disks and upper right corner icon is Smart Data & self tests. 
I do not know what individual parameters mean, but if drive not good, then time for a new hard drive and restore from your backup as drive is broken.

---

### Post by tozden on 2017-07-16
Disk is a 160GB sized SSD. However both windows & ubuntu recognizes it as 8.4MB disk without any partition info.. 

I tried to run Smart Data & Self tests as you suggested, however selection is disabled!?!

Is it possible to recover partial or complete data within this corrupted HDD? If so, I will appreciate if you can suggest me what tools & guidelines I shall look for?

---

### Post by oldfred on 2017-07-16
Is UEFI/BIOS seeing drive?
If drive not seen in BIOS then it cannot be seen by any operating system.

If seen by BIOS then some tools may work, but SSDs run trim which erases unused data.
testdisk & photorec are often used to recover data, but I think drive has to be seen.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

