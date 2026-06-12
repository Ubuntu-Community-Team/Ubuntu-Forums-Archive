---
title: "auto mount hangs at boot"
date: 2021-02-04
forum: General Help
---

### Post by two4two on 2021-02-04
I have around 40 partitions on 16 hard drives.  It is a mix of ext4 and ntfs partitions.  One of the drives (the boot drive) is an SSD.  Seven of the drives are in external USB enclosures.  The rest of the SATA drives are connected to the mobo, either directly or via a PCI-E adapter.  Also, 2 of the drives are IDE -- one is on a PCI-E adapter and the other is on a USB adapter.  Last night when I shut down it took a very long time and spit out a string of messages (which I did not capture).  It never did this before.  This morning when I booted up one of my HDDs had a problem.  It is a 2TB SATA drive with 2 partitions:  1TB ntfs and 1TB ext4.  The ntfs partition will auto mount OK, but the ext4 partition never finishes the auto mount.  I can access the partition with the "testdisk" software even as the automount is still trying to do its thing.  With this utility I can: copy files, make an image of the partition if I want to, display the superblocks and backup or restore them if I want to.  I try to cancel the automount, and it says it is canceled, but it is still active.  I'm stuck here.  I'm thinking of buying a new HDD and using the testdisk utility to copy the existing problem drive to the new drive.  But I'd rather find out what the problem is with the existing drive and fix it.  I'm attaching a txt file with the dmesg output.  And I'm attaching fstab and mtab.  If you need me to attach anything else let me know and I'll do it. The mobo is ASUS PRIME B350-PLUS, BIOS 4011 04/19/2018.[ATTACH]287901[/ATTACH][ATTACH]287902[/ATTACH][ATTACH]287903[/ATTACH]

Just do me a favor and don't question my configuration.  That's not why I'm here.  I just need help with this partition.

---

### Post by dinkidonk on 2021-02-04
Have you tried an extra reboot? Have you checked the file system on the ext4 partition with [e2fsck](https://linux.die.net/man/8/e2fsck)? Does the SMART-data for the drive give any hints that would suggest a lurking drive failure?

---

### Post by two4two on 2021-02-04
I can't do the e2fsck.  It says the device is in use.  This makes sense because automount during boot is hanging and I can't kill the process.

I attached screenshots to show result of e2fsck and disks utility.  The disks utility shows the partition is not mounted, but the system is trying to mount it.  If I could make a change to NOT automount at boot I could maybe run the fsck.  Where can I make this change, in fstab?

---

### Post by CelticWarrior on 2021-02-04
You need to run the command from a live session and even there make sure the partitions to be corrected aren't mounted but unlike when running from the installed system, in the live session everything can be unmounted.

---

### Post by two4two on 2021-02-04
I fixed it.  I edited FSTAB to get rid of auto mount for the partition and booted in recovery mode and executed the e2fsck and repaired the file system.  I rebooted and put the auto mount back in the fstab and rebooted again and it is all fixed now.

---

### Post by dinkidonk on 2021-02-05
> **two4two said:**
> and it is all fixed now.

It is not fixed until you figure out what caused the problem and get rid of that cause. But great that you have sorted it (for now)! :KS

EDIT: Please remember to mark the thread as solved! :)

---

### Post by TheFu on 2021-02-05
USB connections are sometimes flaky.  Vibrations seem to be the cause. Power hiccups can happen too at boot if there isn't sufficient power to all the devices. Would be worth considering using higher capacity drives to lower the power needs.

And if it isn't obvious, get your backups working ASAP!!!  With that amount of storage, it is just a matter of time until data lose happens.

---

