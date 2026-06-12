---
title: "[server] merge non adjacent partitions via command line"
date: 2013-11-06
forum: General Help
---

### Post by sowdust on 2013-11-06
Hi all,

I have a small server running ubuntu with a 80 giga byte hard disk.
The file system / is mounted on the partition /dev/sda5, which is only 8 GB, and is now full.
I have a free 64 GB partition on /dev/sda1. How can I merge these two partitions logically/virtually?

thanks!

---

### Post by ajgreeny on 2013-11-06
I think your main problem will be more related to the fact that your filesystem is on a logical partition and the 64 GB available partition is on a primary one, so you can not merge them even if they were adjacent.
Can we see your complete partition layout from ```
sudo fdisk -l
``` so we can see everything on the disk and how it might be possible to try to help you with a better layout

---

### Post by sowdust on 2013-11-06
sure, this is the device:

```

/dev/sda1   *        2048   137306735    68652344    7  HPFS/NTFS/exFAT/dev/sda2       137308158   156248063     9469953    5  Extended
/dev/sda5       137308160   154171391     8431616   83  Linux
/dev/sda6       154173440   156248063     1037312   82  Linux swap / Solaris

```

thanks!

[i just now notice that formatting the partition didn't go well. It should be ext4, it was originally hosting windows. I'll try to do it now]

---

### Post by oldfred on 2013-11-06
Is it your sda1?
If so do not format it, but unformat it to make it unallocated. Then you should be able to move your extended partition left. Then move sda5 all the way left and then expand right. I would run each separately in gparted  not queue them up.
I do not like moving left as any interruption will corrupt system. So good backups are essential. 

It usually works, but the one time you are in a hurry and do not do the backup it the one time you get a power failure or kick the power switch accidentally and lose system.

Since it looks like sda1 is a lot large, you might be able to just copy sda5 to sda1. But then you have to edit fstab with new UUID and update grub to get it to know it is the new UUID also.

---

### Post by sowdust on 2013-11-08
thanks oldfred;  the only thing I am concerned about is that if I format sda1, won't it delete grub on there?
Following your suggestion I was thinking of : 

1) formatting sda1
2) copying sda5 (filesystem) onto sda1
3) reinstall grub on sda1
4) format sda5 and use it for something 

would copying the whole filesystem just need an edit to fstab?

thanks!

---

### Post by oldfred on 2013-11-08
Unless you are using Windows to boot, sda1 is not involved with booting Ubuntu.

Grub does not use boot flag, but a few BIOS (mostly Intel motherboards) do need a boot flag on a primary partition so you can even start to boot. So we usually suggest a boot flag on a primary partition.

---

### Post by sowdust on 2013-11-08
all right I didn't know that. So do you think the procedure described above would work, with the additional points of:
[LIST]
[*]changin UUID in fstab
[*]updating grup
[*]marking the partition as bootable (I think I have a Dell motherboard)
[/LIST]
?

Thanks!

---

### Post by oldfred on 2013-11-08
It should.
Of course good backups are always recommended. If you have old install still in sda5, you may have to also change UUID of copied partition.

       Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX

---

### Post by sowdust on 2013-12-06
Hello, I am having problems copying the filesystem from one partition to another. I tried with rsync and copy but I get errors both ways, even if I try to exclude the /proc and other sensitive folders.
What would you raccomend being the safest and best way to copy a filesystem? Thanks !

---

### Post by oldfred on 2013-12-06
I only backup /home but get a couple of errors on the mounted files when running.
If doing entire system you need to run it from live system not your working system so everything is unmounted.
I think rsync is best.
If you want an image type backup then clonezilla may be best.
 Full image backups
[http://clonezilla.org/](http://clonezilla.org/)

      
 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

---

### Post by sowdust on 2013-12-14
ok i now see the problem of not being able to back up a system from the system itself. Thank you for pointing it out and also for the funny yet useful article.

---

