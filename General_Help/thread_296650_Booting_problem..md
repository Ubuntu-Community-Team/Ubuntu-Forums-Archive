---
title: "Booting problem."
date: 2006-11-09
forum: General Help
---

### Post by aum11 on 2006-11-09
Have had problems rebooting since using gparted to rearrange harddrive.

When trying to boot Ubuntu, am getting the message:

Error 17: Cannot mount selected partition.

Any suggestions please.

---

### Post by Sef on 2006-11-09
> 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

What is your filesystem, and how did you rearranged your partitions on your hard drive?

---

### Post by aum11 on 2006-11-09
Thanks for the quick reply....have been working on this for hours.

The setup is:

sda2 ntfs  (XP)
sda3 ext3 /
sda5 swap
sda6 ext3 /home

---

### Post by Sef on 2006-11-09
Check out if [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") will resolve your problem.

If not, check out the other two at this post (#8): [Rescue Software]("http://ubuntuforums.org/showthread.php?t=296095&highlight=TestDisk").  (Note: all are no cost.))

---

### Post by hearnden on 2006-11-09
Is this a grub error?

If so, try rebooting and go to a GRUB command-line (it's one of the options you get in the GRUB boot menu), and try something like:

$ (hd0,2)/      <hit tab-tab to see a list of completions>

GRUB will try to mount (hd0,2), i.e. /dev/sda3, and look for files.  You can use this to see which partitions GRUB is able to mount.

Alternatively what if you boot from a LiveCD and try mounting partitions manually?  If you can't mount them in a LiveCD environment, then sounds like your partition table is broken.  If you can mount them in a LiveCD environment but not in GRUB, then that's a problem, and maybe try LILO instead. I know GRUB has some problems with the JMicron PATA->SATA converter, see: [http://ubuntuforums.org/showthread.php?t=234706](http://ubuntuforums.org/showthread.php?t=234706)

---

### Post by dcstar on 2006-11-09
> **aum11 said:**
> Thanks for the quick reply....have been working on this for hours.

The setup is:

sda2 ntfs  (XP)
sda3 ext3 /
sda5 swap
sda6 ext3 /home

Yes, but what **was** it before you changed things?

If you added/deleted partitions then Grub may still looking for the old designation and not the new one.

---

### Post by aum11 on 2006-11-09
Grub error 17 means that the partition exists but that the filesystem type cannot be recognised.

Testdisk finds no problems...says root is Primary bootable and linux.

Gparted on the live disk shows that root is ext3.  Fdisk -l shows all 3 linux partitions looking healthy.  So why is grub coming up with the error?

Any suggestions?

---

### Post by aum11 on 2006-11-10
Dcstar,

all of the partitions are named as previously.

I am starting to think that i will have to do a fresh install...

The partitions look good, but grub insists that the file system type cannot be recognized.

---

### Post by hearnden on 2006-11-10
Are you able to mount those partitions from the live disk?

e.g.

```

$ sudo mkdir /mnt/disk
$ sudo mount /dev/sda3 /mnt/disk

```

If that gives you no problems, then it sounds like a GRUB thing, so maybe try LILO.

---

### Post by hearnden on 2006-11-10
Also, are you sure you know which partition GRUB is trying to mount?  If the location of /boot as changed, then you may need to do a grub reinstall (I've forgotten how GRUB knows where your boot partition is, I think it gets set into stage1 when you do a grub-install). Otherwise, check that the entries in grub/menu.lst set the right partitions:

root (hd0,x)   where x is your boot partition
...
kernel  ... root=/dev/sdaX ...      where /dev/sdaX is your root (/) partition

---

### Post by aum11 on 2006-11-10
Thanks Guys for Your support.:-D 

It ended up that the strange gparted session had deleted a dell fat partition which had thus reduced the addresses for the linux partitions by 1.  This of course stuffed the grub.

Editing the grub got me back into edgy where the grub/menu/lst file could be permanently changed...Thank God!!!!

Lessons?

Be very careful when altering partitions...backup beforehand.
And ask for help on the forum!!!

---

