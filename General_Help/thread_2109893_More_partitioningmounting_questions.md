---
title: "More partitioning/mounting questions"
date: 2013-01-28
forum: General Help
---

### Post by ooleyguy on 2013-01-28
From what I have read so far, if you have Ubuntu installed on SDA1 and then mount partitions from SDB, SCD, etc. they are treated as though they are just part of / (root) and you don't actually switch from one disk to another when saving or moving files. Is that correct?

If that is true, let me give you an extreme instance and tell me if my logic is wrong:

I install Ubuntu on SDA1 and use the entire drive as / (root). During the install, I add a 50 MB SDB1 partition mounted as /home, a 50 MB SDC1 partition mounted as /home and a 50 MB SDD1 partition mounted as /home.

Will my /home directory be 150MB? Will the SDB1 partition get filled up and then Linux automatically start saving into SDC1 and then SDD1 until all three partitions are full?

---

### Post by bab1 on 2013-01-28
> **ooleyguy said:**
> From what I have read so far, if you have Ubuntu installed on SDA1 and then mount partitions from SDB, SCD, etc. they are treated as though they are just part of / (root) and you don't actually switch from one disk to another when saving or moving files. Is that correct?

If that is true, let me give you an extreme instance and tell me if my logic is wrong:

I install Ubuntu on SDA1 and use the entire drive as / (root). During the install, I add a 50 MB SDB1 partition mounted as /home, a 50 MB SDC1 partition mounted as /home and a 50 MB SDD1 partition mounted as /home.

Will my /home directory be 150MB? Will the SDB1 partition get filled up and then Linux automatically start saving into SDC1 and then SDD1 until all three partitions are full?
You can only mount one (1) partition at any mount point (i.e. dev/sdb1 mounted at /home or some such).

[COLOR="Blue"]Edit: If you do mount a second (2nd) partition to a mount point you will hide the first partitions files and directories.[/COLOR]

[COLOR="Blue"]Edit2:  The term drive in Windows speak is a partition or a CIFS share.  In Linux a drive is a block device (e.g a HDD)  The drive (HDD or SSD) is named sd,. sdb, sdc, sdc, etc..  The partitions are the numeric component of the name (sda1 or sda2 or sdb1 or sdb2 etc.) [/COLOR]

You could think of it as [COLOR="Red"]serial[/COLOR] [COLOR="Green"]device[/COLOR]  [COLOR="Blue"]a [/COLOR] number 1 and so on ([COLOR="Red"]s[/COLOR][COLOR="Green"]d[/COLOR][COLOR="Blue"]a[/COLOR]1)

---

### Post by ooleyguy on 2013-01-29
So, if there is a music directory under root where the files will physically reside on the SDA block device and I mount a partition that physically resides on the SDB block device, all the files under /root/home/music would be hidden and I'd only see the files that were on the SDB partition I mounted as /music?

Am I making this way too complicated? Is there an easier way of mounting the hard drives that contain my multimedia so that Ubuntu and the apps I use will store data on those drives instead of on my puny little solid-state boot drive? System wide, not just my user.

---

### Post by dino99 on 2013-01-29
when ubuntu is installed, you get:

- a root partition (/)
- a swap partition
- a /home partition (manual choice, not created by default)

then the system automatically deal with the required pathes using mountall

---

### Post by ooleyguy on 2013-01-29
Well, I did that this morning and then was only able to mount those extra drives on a per user basis, and half the time they mounted, they were read only. I really don't want to go back to windows. I seriously hate it, but when it came to where I could download, install, save, etc. files and folders, it was easy as cake. I just want someone to point me to a document that shows me how to make Ubuntu and its apps do what I want them to do, not what the dev thinks I should be doing.

---

### Post by Impavidus on 2013-01-29
> **ooleyguy said:**
> So, if there is a music directory under root where the files will physically reside on the SDA block device and I mount a partition that physically resides on the SDB block device, all the files under /root/home/music would be hidden and I'd only see the files that were on the SDB partition I mounted as /music?

Am I making this way too complicated? Is there an easier way of mounting the hard drives that contain my multimedia so that Ubuntu and the apps I use will store data on those drives instead of on my puny little solid-state boot drive? System wide, not just my user.
You are making things a bit too complicated.

You can make an empty directory wherever you want to mount the partition with your music, but it has to be accessible by everyone who is allowed to play the music, so don't put it in your own directory (/home/username/music). A good location would be /mnt/music. The directory has to be empty, because any files inside will be inaccessible as soon as you mount your music partition.

Assuming your music is on sdb1 (all lower case), you can add a line to the file /etc/fstab containing something like:```
/dev/sdb1 /mnt/music ext4 defaults
```(It's owned by root, so you need root permissions to edit this file. Also, use **man fstab** to read about the format of this file. Pay attention to the file system type.)
Now the music partition will be mounted at /mnt/music automatically when you boot your computer. The contents of this directory will then reside on physical drive b.

The idea is that linux can use several partitions and merge them all into one big tree. A mount point is a directory physically located on one partition that logically contains the entire directory tree of another partition.

Oh, and the whole idea behind Ubuntu is that your computer does what you want it to do. In my experience it's Windows that does what it's developers think you should be doing.

---

### Post by LewisTM on 2013-01-29
Don't go back to Windows just yet, just read about fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

/etc/fstab is where you tell Linux where to mount your partitions at boot time. It's pretty essential knowledge for anyone who needs to deal with more than the 2-3 standard partitions. With fstab, you can layout your file structure your way. If you want your sdb1 to appear as /Music, that's where you need to put the info.

Cheers!

EDIT: Impavidus beat me to it. I can only add that if you want a nice graphical interface for editing fstab, you can install package **mountmanager**.

---

### Post by furything on 2013-01-29
Hi ooleyguy
Mounting hds follows the below alternatives (guys if I have missed anything please add)

From the boot partition you get the root /

Under here there are lots of folders but by default if you plug in an extra drive and use the file manager to mount it the drive gets mounted from root in media so /media/identifier of drive (this will be the uuid)  - this could be sdb or even an external hard drive. If sdb you can access drive from /dev/sdb as well as from /media

When you use the mount directory /mnt what you are actually doing is creating a new folder and then calling the 'mount' command to make another hard drive/partition accessible. You can then navigate to that drive as /mnt/new directory from root. As said only one hard drive/partition should be mounted to a directory so take care.

This is the default suggestion for mounting points BUT you could do as you say 'mount' in your music directory in your home directory - AGAIN only ONE drive/partition. So mount drive sdb to '/home/your login NOT root/Music note Music case as linux is case specific.

If you want to make a drive/partition as a permanent mount then you need to add it to fstab. The best thing to do is experiment with mount to create the directory point you want. Once you are happy with that choice then edit fstab to make it permanent following the link LewisTM gave you. Don't use usb as I have found this way a little unreliable and the system refusing to boot when the usb hard drive is not ready.

As an example I have edited my fstab so my mythtv music folder on a slave actually points back to the primary backend server
Cannot remember exact syntax but something like 
ipaddr:/var/lib/mythtv/music /var/lib/mythtv/music nfs auto
(nfs is means a network share)

The important thing to remember is that the folder you are mounting to (as you have been told in this thread) becomes hidden so you need to move the content away from it before remapping. _**[COLOR=Red]DO NOT[/COLOR]**_ use the linux directories as you will break your system.
Always use /mnt new directory or an appropriate user directory (your user not root).

---

### Post by ooleyguy on 2013-01-29
Excellent assistance folks. The system linux uses to do the files has finally sunk into my thick skull. I still have a bit of learning when it comes to all the command line things that happen in terminal. I haven't regularly used a command line since Windows 95. 

For instance, somehow I removed my sudo privileges while trying to give my group read/write access to the documents and downloads folder I created by mounting them. Solved it, but felt pretty dumb.

---

