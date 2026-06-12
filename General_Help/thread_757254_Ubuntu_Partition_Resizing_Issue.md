---
title: "Ubuntu Partition Resizing Issue"
date: 2008-04-16
forum: General Help
---

### Post by TroyDowling on 2008-04-16
Hey Ubuntu forum goers,

I recently have been taking steps toward the total UNIXification of my desktop computer. At the moment I'm running an XP/Hardy dual boot setup on a 500GB drive. Initially, Ubuntu sat on a measly 40GB, but as I grew into the OS I found I now needed more room. 'Not a problem' I thought as I popped into my Paragon Partition Manager Boot CD v9.0 and resized Windows (0,0 NTFS) down a few hundred gigabytes and dropped that free space onto Hardy (0,1 EXT3). The operation completed successfully, but when I went back into Ubuntu it doesn't recognize this new free space! The partition capacity reads the incorrect size in System Monitor as the old 36.7GB but 'parted' sees the partition correctly.

```
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      32.3kB  290GB  290GB   primary  ntfs         boot 
 2      290GB   496GB  206GB   primary  ext3              
 3      496GB   500GB  3997MB  primary  linux-swap  
```

If I go back into Paragon, it shows the partion as the right size, just nearly completely full. I'm pretty much bedazzled now and don't know what to try. Any help?

---

### Post by nicedude on 2008-04-17
It looks to me like paragon partition manager is what goofed up your ext3 partition (windows and linux partition tools don't always work well on the other OS's disks). I have had a few things happen similar to yours and its always when I was messing with a partiton made by one operating system with a tool from another. 

Boot Ubuntu from a live CD (as in a live Ubuntu install disk because we need the partition in the unmounted state to modify it) from the live CD bootup desktop open the synaptic package manager (system -> administration -> synaptic package manager) and install gparted (this is parted but with a GUI interface which reminds me of Partition Magic 8's interface. gparted still uses the same library to do its work as parted does so I would recommend it as it is much harder to make a mistake) just search by name only for "gparted" in synaptic search (without quotes). After you get gparted installed use it to cut all the space you added to partition #2  ie. change partition 2 back to the 36.7 gb and leave the rest as empty space at the end of the #2 partition, once your sure it looks right then in gparted's press the green check mark called apply. After it is done resizing reboot your PC and log back into Ubuntu live cd again. Open up gparted again and choose to increase the size of partition #2 by adding the free space you cut off of it before, click the green checkmark again when all looks right and after it gets done reboot. This time when you boot back into Ubuntu you can remove the live CD and boot Ubuntu from partition #2 you should have all your partitions back the way you intended them and they should be accessible once again. 

I would only use the partion tool suite that made a given partition to work on it in the future to keep this from happening again. Man I hope you can follow all that and get your disk back in order. If you have any problems just PM me and ill try to help some more.

---

### Post by TroyDowling on 2008-04-17
Ha, I'm well aquainted with the parted series. =] Thanks for the detailed instruction set anyways, it should be a nice article that sits around on the forum for anybody else. Judging by your solution though, I think I should have been more clear; that's my fault. The partition HAS resized correctly. GParted/Parted/Paragon/PartitionMagic/etc ALL recognize the CORRECT size of the partition. However, the operating system itseld sees the incorrect size. I'll try out your steps anyways in case I missed something anyways. Included is a snap of my filesystem layout from the OS' eyes...

[IMG]http://i15.photobucket.com/albums/a353/Skwattingdog/FilesystemUsage.png[/IMG]

Note that the space was taken from sda1 (Windows) and plunked into sda2 (Ubuntu). The actual steps taken were as follows (if it's prudent):

1) Downsize sda1, free space is now between sda1 and sda2
2) Move sda2 so that free space is at the end
3) Increase size of sda2 to envelope the space.

---

### Post by TroyDowling on 2008-04-20
To the readers,

I basically gave up on trying to fix what was wrong. I found out, with the generous help of niceguy, that my partition was borked from the point I used Paragon to manipulate it. Since my previous post, I just formatted the drive completely and recovered my Ubuntu partition from an Acronis backup I have. Now I have tonnes of space for Ubuntu, and not the problems of Windows to deal with.

Thanks all,
Troy.

---

