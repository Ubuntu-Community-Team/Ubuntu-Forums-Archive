---
title: "[SOLVED] /bin/sh: can't access tty; job control turned off"
date: 2008-03-13
forum: General Help
---

### Post by tomid on 2008-03-13
There are a few threads already with this title, and I've skimmed them all but mostly they talk about moving hard drives about. I haven't opened up my computer recently, and Ubuntu was loading up fine a couple of hours ago. I have contributed to another post regarding the partitioning of my Ubuntu drive to give Windows more space, though I've not yet downloaded the gparted livecd file (on this working computer).

I don't think I did anything serious last time Ubuntu was loaded up. I was in Windows, defragmenting the Windows partitions (separate hard disk), and also looking to see if I can partition Ubuntu from Windows. I couldn't find a way and don't think I did anything which could have cause the current problem. After defragmenting was complete I restarted into Ubuntu and encountered my problem for the first time. Tried the recovery mode and met the same screen.

The problem begins with:
Uncompressing Linux... Ok, booting the kernel.
mount: Mounting /dev/sdb1 on /root failed: Invalid argument
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
Busybox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)


I hope that isn't too boring or wordy, though expect it is.

Ultimately, has my Ubuntu died? It probably is a good opportunity to upgrade to the latest Ubuntu (was Edgy Eft). Or is this a problem which can be solved? I don't think I have any unbacked-up data on that disk. But I'd rather look through my files before I format the disk. Is that possible?

---

### Post by kyphi on 2008-03-13
I do not know what you have done to your current installation nor how to fix it.

However, you can use the live CD to look at the files on your hard drive (if it is accessible) and save them to a USB storage device.

---

### Post by tomid on 2008-03-14
Thanks for your suggestion.

I have made and loaded up an Ubuntu 7.10 live disk. I can access my Windows NTFS and FAT32 partitions from there (something I couldn't do with my previous Ubuntu installation (6.06 or 6.10)), but the existing Ubuntu partition won't mount. The following message comes up:

```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so
```

I will open up the computer to make sure all the cables are connected then, if that doesn't solve it, I will format that whole disk and start again with 7.10.

Shortly before the fault occurred, I formatted a previously unused partition on the Windows disk and made it FAT32 because my (Apress) Ubuntu book stated that this filesystem could be accessed from both Windows and Ubuntu. It appears that 7.10 has no problem accessing the old NTFS partition. Maybe, the creation of the FAT32 partition caused the fault, but I then loaded up Ubuntu and tried to access FAT32 (without success, but with no crashing either). I think the later defragmenting of the two Windows partitions caused the problem.

Thanks again.

---

### Post by kyphi on 2008-03-14
> I think the later defragmenting of the two Windows partitions caused the problem.Most likely.

For future reference, always defrag your Windows drive before repartitioning.

You can see your partitions in Windows by right clicking on the computer icon, choosing Manage from the dropdown menu and then Disc Management.

In Ubuntu use ```
sudo fdisk -l
```

You could also try ```
sudo touch /forcefsck
``` and then reboot to force a file system integrity check.

If all else fails, reinstall Ubuntu.  I assume that Windows boots normally.

---

### Post by tomid on 2008-03-15
Thanks for your help. Yes, Windows works fine. I'm a bit hesitant about reinstalling Ubuntu now, as there are swap files to think about and what not. I think I may install Ubuntu in it's own mini-partition next time, so if it goes wrong again I won't necessarily lose data.

---

