---
title: "Reformat NTFS disk to use as backup to Ubuntu"
date: 2016-04-12
forum: General Help
---

### Post by flyingsolo on 2016-04-12
I'm trying to reuse an external drive that previously was formatted in OSX but now has been emptied.
I intend to  use it as backup to my Ubuntu 14.04 using DejaBup but I don't have Write access to the disk in Ubuntu.

I need suggestions on how to proceed. Thank you.

---

### Post by yancek on 2016-04-12
> I intend to  use it as backup to my Ubuntu 14.04 using DejaBup but I don't have Write access to the disk in Ubuntu.


As a general rule, anything outside your /home/user directory needs root or permissions so you need to use sudo.  You can also change ownership of the partition(s) on the drive.  Various partitions and external drives will be available under the /media/username directory so you will first need to determine which is the one you want.  You should format the partition(s) with  Linux filesystem such as ext4.

---

### Post by flyingsolo on 2016-04-12
So, if I cd to the correct drive, what command do I use to format the drive? I've not done formatting via command line before.

---

### Post by yancek on 2016-04-12
If you have your Ubuntu installation DVD, you have GParted on it and you can use it.  Or you can download it to Ubuntu and use it from your installed Ubuntu on a secondary drive.

If you want to do it manually from a terminal, the link below explains it and gives some examples.

[http://www.thegeekstuff.com/2013/01/mke2fs-examples/](http://www.thegeekstuff.com/2013/01/mke2fs-examples/)

---

### Post by SeijiSensei on 2016-04-13
Do you only intend to use this drive with Linux, or might you want to see it from a Windows system as well?  For Linux only, you can format a drive with the current standard ext4 filesystem like this:
```
sudo mkfs -t ext4 /dev/sdX
```
where "X" refers to a drive/partition combination like /dev/sdb1 for the first partition ("1")  on the second hard drive ("b").

You might need to repartition the drive first.  I usually rely on fdisk for this task from the command prompt.  Use "sudo fdisk /dev/sdb" then enter commands by letter.  Note that this command takes the entire drive as a parameter like /dev/sdb, not a single partition like /dev/sdb1.

```

p - list the partitions on the drive
d - delete a partition
n - create a new partition
t - set the partition's type 
w - write a new partition table to the drive

```
For an existing drive, I'd start with "p" to list the partitions, then use "d" repeatedly to delete partition 1, 2, etc., until they are all removed.  Then make a new partition with "n" and accept the defaults offered so the partition spans the entire drive.  Check the results with "p".  It should have type "Linux" by default. If not, type "t", then enter the code 83 for Linux (type "l" for a complete list). Now type "w" to write the new partition table to the drive, then format it with mkfs as above.

If you want to create an NTFS filesystem on the drive, I'd only do that from Windows myself.  In fact, there isn't an NTFS formatter as part of the standard array of mkfs utilities.  You can create a DOS-formatted drive ("FAT32") that both Linux and Windows can read with the command:
```
sudo mkfs -t vfat /dev/sdX
```
That's the format that most devices like USB thumb drives come with by default.

---

### Post by flyingsolo on 2016-04-13
Thanks for your help (all above!). I did reformat the drive to ext4 as this will only be used for the linux system backups and not swapped back to OSX or others.
I still was having issues with ownership of the disk and denied access to write to the 'new' disk. Before I figured out how to use chown to reassign ownership, I found an easier method via using "Disks" program already on my system.
It was pretty straightforward to edit anything on the disk including partitions, formatting, ownership...I didn't know about this before! 
Oh well, still learning even though I've been using linux (ubuntu, mainly) for lots of years.

---

