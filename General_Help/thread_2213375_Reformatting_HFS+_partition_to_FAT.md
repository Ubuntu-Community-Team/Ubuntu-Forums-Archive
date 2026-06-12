---
title: "Reformatting HFS+ partition to FAT"
date: 2014-03-26
forum: General Help
---

### Post by aneblanc on 2014-03-26
I have an older ipod 30gb. It has a 30gb HFS+ partition that I like to use to store my own data. This partition is read-only. 

If I reformat it into a FAT partition will the ipod still work as an MP3 player? Should I use another format? I am using the Disk Utility program that comes with Ubuntu.

Ubuntu 12.04

---

### Post by PartisanEntity on 2014-03-26
This question sounds like it is more suitable being asked over at an Apple/Mac forum. I doubt many users here will know whether you can change the file system on a non-Ubuntu/Linux related product without destroying it.

---

### Post by tgalati4 on 2014-03-26
Yes, you will lose any files on the iPod.  You can format it to FAT32 with *gparted*.  You will then have to find a Windows machine to load iTunes and then load the update (firmware) files to the iPod so that it will now play music as a normal iPod, but with FAT32 instead of HFS+.  You can also install jsymphonic or rockbox as alternate methods to play music and manage the files.

---

### Post by ajgreeny on 2014-03-26
A quick google for my own information suggests that there is no problem.

[https://www.google.co.uk/search?q=fat32+on+ipod%3F&ie=UTF-8](https://www.google.co.uk/search?q=fat32+on+ipod%3F&ie=UTF-8)
[http://www.ehow.com/how_7312383_restore-fat32-system-ipod.html](http://www.ehow.com/how_7312383_restore-fat32-system-ipod.html)
[http://www.patrickmin.com/linux/tip.php?name=convert_ipod](http://www.patrickmin.com/linux/tip.php?name=convert_ipod)

---

### Post by Lars Noodén on 2014-03-26
If you turn off journalling, then you should be a ble to write to HFS+  and your files would still keep their permissions.  If you use FAT, they will lose their permissions and the filesystem itself is more vulnerable to failure.

---

### Post by aneblanc on 2014-03-26
> **tgalati4 said:**
> Yes, you will lose any files on the iPod.  You can format it to FAT32 with *gparted*.  You will then have to find a Windows machine to load iTunes and then load the update (firmware) files to the iPod so that it will now play music as a normal iPod, but with FAT32 instead of HFS+.  You can also install jsymphonic or rockbox as alternate methods to play music and manage the files.

I wasn't probably very clear, sorry. 
The ipod has an Apple Partition Map in 2 sections, 127kb for the Partition Map, 168mb for the Apple MDFW (?) and the remaining ±30gb for the HFS+ file system.

I use Ubuntu 12.04. My question is can I reformat the file system (Ext4 or FAT or NTFS, which one?) without touching the 2 other sections of the drive and expect the ipod to behave like an MP3 player?

---

### Post by aneblanc on 2014-03-26
> **Lars Noodén said:**
> If you turn off journalling, then you should be a ble to write to HFS+  and your files would still keep their permissions. 

Any clue how to turn off journaling?

---

### Post by Lars Noodén on 2014-03-26
I've only ever done it via OS X

```

diskutil disableJournal /Volumes/TheVolumeName

```

It can also be done with a click in the Disk Utility. 

But for partitions I've created in Linux, journaling is already off.  There is rumor to be a utility you can compile to turn it off and there is one other report here: [http://solie.blog.undip.ac.id/2009/11/12/how-to-disable-journaling-on-hfs-partition-via-linux/](http://solie.blog.undip.ac.id/2009/11/12/how-to-disable-journaling-on-hfs-partition-via-linux/)
However I haven't tried either way yet.

---

### Post by aneblanc on 2014-03-26
> **Lars Noodén said:**
> [http://solie.blog.undip.ac.id/2009/11/12/how-to-disable-journaling-on-hfs-partition-via-linux/](http://solie.blog.undip.ac.id/2009/11/12/how-to-disable-journaling-on-hfs-partition-via-linux/)

What does the first "y" stand for in:

# fsck.hfs -fy /dev/sdxy ?

I actually found and tried it this morning but it didn'twork, though I'll try it again.

---

### Post by Lars Noodén on 2014-03-26
The -y stands for attempt to repair damage that is found.  [fsck.hfs](http://manpages.ubuntu.com/manpages/saucy/en/man8/fsck.hfs.8.html) and fsck.hfsplus are in the package hfsprogs so you will have to have that installed for it to be available, if you haven't done so already.

---

### Post by aneblanc on 2014-03-26
Doesn't seem to work.

---

### Post by aneblanc on 2014-03-26
That's what I get:

[I] sudo fsck.hfs -fy /dev/sdb3
** /dev/sdb3
** Checking HFS Plus volume.
** Checking Extents Overflow file.
** Checking Catalog file.
** Checking Catalog hierarchy.
** Checking Extended Attributes file.
** Checking volume bitmap.
** Checking volume information.
** The volume XXXXXXXXX appears to be OK.
[/I]
But still read-only when I remount

---

### Post by Lars Noodén on 2014-03-26
The recipe there had two commands back to back.  But as mentioned, I haven't tried them.  If they do not work, then there was a short c program floating around to try.  Do you have an OS X machine or partition you can boot instead?

---

### Post by aneblanc on 2014-03-26
> **Lars Noodén said:**
> The recipe there had two commands back to back.  But as mentioned, I haven't tried them.  If they do not work, then there was a short c program floating around to try.  Do you have an OS X machine or partition you can boot instead?

Do you mean I should have tried first the fsck.hfsplus then fsck.hfs commands?

No I don't have a mac nor a mac partition.

---

### Post by PartisanEntity on 2014-03-26
I can confirm that if you created a HFS+ partition using gparted, journaling wil be off by default.

On the Ubuntu side, make sure hfsprogs is installed

```
sudo apt-get install hfsprogs
```

Then mount the drive like so, example:

```
sudo mount -t hfsplus -o force,rw /dev/sdx# /media/mntpoint
```

(Notice that "#" should be the number corresponding to the external drive)

I am currently using an internal HFS+ partition on my iMac to share files between Ubuntu and OSX. (I had to also change the UID of my Ubuntu user account to 501 to match that on OSX)

---

### Post by aneblanc on 2014-03-26
> **PartisanEntity said:**
> I can confirm that if you created a HFS+ partition using gparted, journaling wil be off by default.

On the Ubuntu side, make sure hfsprogs is installed

```
sudo apt-get install hfsprogs
```

Then mount the drive like so, example:

```
sudo mount -t hfsplus -o force,rw /dev/sdx# /media/mntpoint
```

(Notice that "#" should be the number corresponding to the external drive)

I am currently using an internal HFS+ partition on my iMac to share files between Ubuntu and OSX. (I had to also change the UID of my Ubuntu user account to 501 to match that on OSX)

This sounds great! 

Do I understand correctly: I can simply reformat my HFS+ partition as HFS+ and get rid of the read-only attribute?

Hfsprogs is installed. I also installed gparted.

What would be the command to reformat the HFS+ partition with gparted?

---

### Post by PartisanEntity on 2014-03-26
You don't need a command for gparted, since it is a GUI simply launch it, find the partition you want to reformat and select HFS+ from the list of possible file-systems. gparted will then create a non-journaled HFS+ partition. Just be careful and make sure you have selected your external partition before you do anything, the drop down for the list of partitions and hdds is on the top right of the window.

---

### Post by aneblanc on 2014-03-26
Gparted doesn't recognize the partition table and so only the entire disk can be formatted and not only the existing HFS+ partition as I had hoped.

---

### Post by aneblanc on 2014-03-26
With the Ubuntu's Disk Utility I have the following possibilities: formatting the volume, editing the partition or deleting the partition. Shouldn't I start there?

I am poking in the dark.

---

### Post by PartisanEntity on 2014-03-27
Hmm but if as you say only the entire drive on the ipod can be formatted/edited, I have no idea if that is going to delete the ipods operating system partition.

---

