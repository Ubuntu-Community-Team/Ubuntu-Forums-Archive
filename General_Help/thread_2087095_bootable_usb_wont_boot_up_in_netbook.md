---
title: "bootable usb wont boot up in netbook"
date: 2012-11-22
forum: General Help
---

### Post by louisgonick on 2012-11-22
Greetings,

I've been trying to boot ubuntu 12.10 from a usb on a netbook I recently purchased. 

After I click on 'try ubuntu' I get a black screen with a blinking cursor. I tried that same usb on my other laptop and it booted up with ease. In addition to that, I've tried othre distros like Fedora, and they boot with no problem on my HP mini. 

What may be that prevents ubuntu from booting up on my netbook? Hardware incompatibility? 

Any suggestions are appreciated.

---

### Post by dcstar on 2012-11-22
> **louisgonick said:**
> Greetings,

I've been trying to boot ubuntu 12.10 from a usb on a netbook I recently purchased. 

After I click on 'try ubuntu' I get a black screen with a blinking cursor. I tried that same usb on my other laptop and it booted up with ease. In addition to that, I've tried othre distros like Fedora, and they boot with no problem on my HP mini. 

What may be that prevents ubuntu from booting up on my netbook? Hardware incompatibility? 

Any suggestions are appreciated.

Sometimes an existing Linux partition can cause this sort of thing, is there one already on the hard disk?

---

### Post by cjhabs on 2012-11-22
Some netbooks can't boot off a USB drive > 2Gb

---

### Post by louisgonick on 2012-11-22
> **dcstar said:**
> Sometimes an existing Linux partition can cause this sort of thing, is there one already on the hard disk?

No, this is a brand new computer. 

It has the standard HP recovery partition (D), but no other linux partitions. 

> **cjhabs said:**
> Some netbooks can't boot off a USB drive > 2Gb

Fedora worked pretty well from a USB drive. My netbook has 2GB of DDR3 RAM and the drive I used has 4GB of space. 
--------------
So I discovered that the Atom processor I have (N2600) has a 64 bit architecture. I used to get the blinking cursor on the black screen with the 32bit iso image, but after trying with the 64bit image (which apparently only is for AMD chips)I simply got a message saying "This kernel is for X86 processors and an i686 chip was detected, please use a kernel appropriate for your system" Or something within those lines. This happens as soon as I boot up, whereas with the 32bit version, I do get to the GUI.

---

### Post by oldfred on 2012-11-23
Often a video issue. Do you have the same video card/chip in both systems?

       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
Sometimes other boot options are required as work arounds for new hardware.

---

### Post by louisgonick on 2012-11-23
I got ubuntu to boot up with 12.04 32  bit!

Now, I have a question. Once I try to install, I don't get the option 'install windows alongside with ubuntu'. I do want to keep windows and I don't want to pick 'something else' because I'm scared to mess with partitions. 

How could I get this feature back?

---

### Post by oldfred on 2012-11-23
Post this:

       sudo parted /dev/sda unit s print

---

### Post by louisgonick on 2012-11-23
> **oldfred said:**
> Post this:

sudo parted /dev/sda unit s print
```

Model: ATA Hitachi HTS54323 (scsi)
Disk /dev/sda: 625142448s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type     File system  Flags
 1      2048s       409599s     407552s     primary  ntfs         boot
 2      409600s     595189759s  594780160s  primary  ntfs
 3      595191808s  624928767s  29736960s   primary  ntfs
 4      624928768s  625139711s  210944s     primary  fat32        lba

```

This is what each partition is (I believe)
1. is system
2. is C (Windows 7)
3.HP recovery
4. Hp tools

As you may see, I have four partitions as most new computers have nowadays. I was reading some workarounds for this that involved deleting the partitions, but involved a rather complex process of several backups. From what I have read, all partitions are equally important (Hp tools has the Bios in it)

---

### Post by louisgonick on 2012-11-23
At first I reduced the size of C to give space for Ubuntu, but then I realized that I already had 4 partitions, which is the limit, so I reverted my drive to the original parition layout.

---

### Post by oldfred on 2012-11-23
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

---

### Post by louisgonick on 2012-11-24
Thanks.

Now I must find a way to create backup DVDs without a DVD drive :)

---

### Post by oldfred on 2012-11-24
Time to invest in a flash drive or two. They have really dropped in price lately.

---

### Post by louisgonick on 2012-11-24
Hmm... apparently, I found a way to merge RECOVERY (D) with the C partition. I'll try it out and post any results.

---

