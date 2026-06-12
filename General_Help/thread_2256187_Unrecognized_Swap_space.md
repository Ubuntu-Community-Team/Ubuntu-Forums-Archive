---
title: "Unrecognized Swap space"
date: 2014-12-10
forum: General Help
---

### Post by tracy5 on 2014-12-10
I am new to this forum, mostly because I search thoroughly through before posting a question. Essentially this is the problem...

I installed Ubuntu trying to install alongside windows, but I did not see that option available in the usb install for 14.10 installation, so I created a 12gb partition on my hard drive and installed it there. It prompted me to select a drive as swap space. The description said that it would use the free space on the drive to use swap space for when there was not enough RAM available.... I have 12gb of ram, but I thought "It couldn't hurt"... anyway I installed Ubuntu with no problems but I could not dual boot the windows 7 OS. I looked through all the forums saying to use a recovery disk, which I did but the 900gb that was my windows partition was unrecognized and I could not repair it. I then reinstalled windows 7 on that same partition where I installed ubuntu thinking that I would just go in, recover the data on the 900gb and reinstall ubuntu and be fine, but the partition that is there with the 900gb has no label or file system, which I expected to happen, but I have NO idea how to recover my data. Can anyone assist me? I do not want to lose that much data. It is mostly games and stuff, but there are important files for work and school there.
[IMG]http://i298.photobucket.com/albums/mm267/guardian715/Diskpart.png[/IMG]
This is the partition showing in diskpart as 918 GB which I referred to as 900 GB

[IMG]http://i298.photobucket.com/albums/mm267/guardian715/Disk.png[/IMG]
This shows disk management saying that there is no volume or file system

---

### Post by sudodus on 2014-12-10
Welcome to the Ubuntu Forums :-)

Too bad that the Windows partition was damaged. But there are tools

1 - testdisk - to repair the file system
2 - photorec - to recover the files without a file system

You find them (and descriptions) at the following link

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

1 - ***testdisk***

If it is ***very*** important to recover the data, I suggest that you start by cloning the drive with Clonezilla before using testdisk.

Then try to recognize and then if possible modify the partition table and file system metadata, which might bring back the NTFS file system. I have not used testdisk myself, but there are several success stories at the Ubuntu Forums (as well as several failures).

2 - ***photorec***

This tool can recover files from the data stored on the 'disk surface' even when the file system metadata is destroyed (if testdisk did not work). It can identify typical beginnings of files of certain kinds. I suggest that you do not try to recover everything, but focus on some particular file types. They will be recovered without file names, so it is a lot of work to identify them, but it is possible. I have used photorec, and it worked for me. There are many success stories, but if the data is overwritten, there is nothing to do. I think it is hard to recover files that are fragmented.

***Do not mount*** the partitions where you want to recover files!!! Save the files in another drive, for example an external drive.

---

### Post by tracy5 on 2014-12-10
There are some strange things happening with that... Would you be able to communicate with a faster option. With Skype or an IM service?

---

### Post by tracy5 on 2014-12-10
Alright I used the testdisk, but it prompted me to restart the system, but when I did, it said missing operating system. I used the logical partition I created but it only has 300mb free now, so I think that May be why it will not start

---

### Post by sudodus on 2014-12-10
I suggest that you run testdisk from a separate drive, for example a USB boot drive (if you have one). You can use your Ubuntu install DVD drive too (and install testdisk and photorec into it temporarily)

---

### Post by tracy5 on 2014-12-10
Would it be right to structure the file system that was swap for the Ubuntu?

---

### Post by tracy5 on 2014-12-10
> **sudodus said:**
> I suggest that you run testdisk from a separate drive, for example a USB boot drive (if you have one). You can use your Ubuntu install DVD drive too (and install testdisk and photorec into it temporarily)
I did that and I think it worked, but I get stuck at post screen now.

---

### Post by sudodus on 2014-12-11
> **tracy5 said:**
> Would it be right to structure the file system that was swap for the Ubuntu?

Any primary or logical partition can be made to be a container for swap or for a file system. Or you can remove it and re-use the disk space for something else. Use ***gparted*** (when booted from another drive) to do it. File systems should unmounted and swap space should be 'swapped off' (with the command swapoff).

---

### Post by sudodus on 2014-12-11
Here is the reply:

> **tracy5 said:**
> I did that and I think it worked, but I get stuck at post screen now.

Please describe how far you reach in the boot process (what do you see on the screen until it gets stuck)?

Which version (14.04.1 LTS) and flavour (standard Ubuntu, Kubuntu, Lubuntu, Xubuntu) are you trying?

Did you check with md5sum that the download was good?

And you booting from CD/DVD or from USB?

Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

When I (and other people) know about these things, we can give better advice.

-o-

A crude guess would be that you have problems with the graphics  chip/card or that you have problems with booting at all, but there might  be a completely different problem. Now your first task is to make your  computer boot and run well from an external drive (CD/DVD/USB). After  that we can focus on recovering your data from the internal drive.

---

