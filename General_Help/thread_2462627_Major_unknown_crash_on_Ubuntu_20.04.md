---
title: "Major unknown crash on Ubuntu 20.04"
date: 2021-05-24
forum: General Help
---

### Post by Semn on 2021-05-24
Hi, I had a major crash on sem-Latitude-7490 Ubuntu 20.04, where the media player in Chrome got stuck, and the whole desktop froze. After several restarts I am able to run the system again, after I did a safe reboot and did some cleaning etc, but without that any errors were found. Then I wanted to do a disk check, but when I looked for the names of my disks, but I can't find which disk to do the check on. Can someone identify it by the given snapshot?

Thanks


[IMG]https://drive.google.com/file/d/1mDx0A1YukVvBh2vWBa8hjEGoJWyNrHz-/view?usp=sharing[/IMG][https://drive.google.com/file/d/1mDx0A1YukVvBh2vWBa8hjEGoJWyNrHz-/view?usp=sharing](https://drive.google.com/file/d/1mDx0A1YukVvBh2vWBa8hjEGoJWyNrHz-/view?usp=sharing)

---

### Post by dddman on 2021-05-24
I also get the occasional browser freeze and have to reboot.  You want to run a disk check why not use smart?

[https://help.ubuntu.com/stable/ubuntu-help/disk-check.html.en](https://help.ubuntu.com/stable/ubuntu-help/disk-check.html.en)

---

### Post by Semn on 2021-05-24
thanks will do!

---

### Post by TheFu on 2021-05-24
The tool to validate file systems for native Linux file systems is called fsck.  To run it, the file system cannot be mounted.  That makes doing this difficult for the root file system - where the OS sits.  In the Advanced menu for Grub, there is a maintenance mode or recovery mode choice. Pick that. In there should be a menu item to check all file systems. Pick that.  

There is also a way to edit the grub command line to force the fsck for the root file system.  In /etc/default/grub there is a line. Make it look like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="fsck.mode=force fsck.repair=yes"
```
That will force an fsck on the OS partition/file system at every boot until removed.  There may be other options in your GRUB_CMDLINE_LINUX_DEFAULT line, so be certain to keep those and ADD the options above, if you are going this way.
Then run **sudo update-grub** to get it pushed into the grub boot area.

For UEFI booting that doesn't use Grub, I don't have any clue. Sorry.

Using **smartctl** to monitor each physical storage device weekly is a good idea too.  Keep a few versions of the output so you can easily compare any changes over time.  It is also possible to setup smartctl to run tests weekly and monthly automatically, then email the test results.  I do short tests weekly and long tests monthly.  Getting an email a few days before a HDD fails is better than not getting any warning at all. Chances are, by that time, some data has been lost, so don't think any of this replaces the need for automatic, versioned, backups. Those are mandatory, regardless of the storage - including RAID.

---

### Post by mIk3_08 on 2021-05-24
> **Semn said:**
> Then I wanted to do a disk check, but when I looked for the names of my disks, but I can't find which disk to do the check on. Can someone identify it by the given snapshot?

try to run this command;
```
sudo fdisk -l
```
and when you see some result like this below; 
```
Device     Boot           Start         End     Sectors   Size  Id Type
/dev/sda     *     2048 466547886    468823460            483.9G 83 Linux
```
If you see some Device "/dev/sda" well that is your drive where your Ubuntu Linux system installed.

---

### Post by tea for one on 2021-05-25
[COLOR="#0000FF"]/dev/nvme0n1p4[/COLOR] is your root partition.

[COLOR="#0000FF"]/dev/nvme0n1p1[/COLOR] is your EFI partition.

---

