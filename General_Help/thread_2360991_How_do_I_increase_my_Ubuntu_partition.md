---
title: "How do I increase my Ubuntu partition"
date: 2017-05-10
forum: General Help
---

### Post by Odense on 2017-05-10
I have a dual boot laptop with Windows 10 and Ubuntu 16.04
Windows was preinstalled and I have added Ubuntu later.
In general it works well.

I would however like to move some space from the Windows partition to the Ubuntu partition. I have reduced the Windows partition but Gparted will not let me increase the Ubuntu partition.

How do I get the result I want ?

---

### Post by yancek on 2017-05-10
Before reducing the windows partition, did you run Disk Defragmenter?
Did you use windows Disk Management to shrink the windows partition?  Always best to use windows tools to change windows, Linux tools to change Linux.
After shrinking the windows partition, did you reboot and run:  chkdsk /f?  Good idea any time you modify a windows partition.
Did you leave your windows system hibernated or with fastboot on before running GParted?  You need to turn hibernation/fastboot off.
It would help if you posted an image or link to an image of the GParted screen for the drive in question.

---

### Post by kansasnoob on 2017-05-11
Are you attempting the resize using a live DVD/USB? You can't resize mounted partitions so Gparted won't work from the installed Ubuntu OS.

---

### Post by vscwap on 2017-05-11
yancek and kansasnoob has given you all the info you need.

Don't for get to backup both win10 and Ubuntu as you may lose data.

Just boot from a live media (like a DVD or USB) and use gparted to do what you want.

HTH.

---

### Post by Mark Phelps on 2017-05-11
Since it appears you have already made the mistake of running GParted against the Win10 filesystem, then follow yancek's advice about running CHKDSK in Windows before you do anything else -- to confirm that it will still boot OK.

---

### Post by Odense on 2017-05-11
You are right - I left out too much info in the original question. I also HAD made the screen-shots but forgotten to attach them.
I DID shrink the Windows Partition with Windows Disk Management - but without defragmenting. It is a SSD and I heard that is not good for those. Is that a myth ?
I did not use  chkdsk /f - why is that a good idea ?
I just made a normal reboot and picked Ubuntu instead of Windows - how do I turn hibernation/fastboot off ?
i will attach the screen-shot now - if possible both screen-shots.

I HOPE the main answer is given by kansasnoob and vscwap - that I naturally need to boot from a USB stick to increase the Linux partition. I kind of knew that - but I DID try to do it from the installed OS.


> **yancek said:**
> Before reducing the windows partition, did you run Disk Defragmenter?
Did you use windows Disk Management to shrink the windows partition?  Always best to use windows tools to change windows, Linux tools to change Linux.
After shrinking the windows partition, did you reboot and run:  chkdsk /f?  Good idea any time you modify a windows partition.
Did you leave your windows system hibernated or with fastboot on before running GParted?  You need to turn hibernation/fastboot off.
It would help if you posted an image or link to an image of the GParted screen for the drive in question.

---

### Post by yancek on 2017-05-11
Running chkdsk after modifying a windows partition is to make sure there are no problems with the partition filesystem.  Hopefully, running it returns no errors.

Turning hibernation on/off is usually done in the BIOS on boot and the method varies with manufacturer.  Check your owners manual.  You may also have some option in windows but I don't use it so can't help with that.

The key icon to the right of /dev/sda7 and /dev/sda8 means those partitions are mounted and you can't change them.  You need to unmount them first.  You will not be able to do that if you are running GParted from the installed Ubuntu.  Also, I don't see any free space to which you can extend the Ubuntu partition before it.  To increase the size of a partition, you need adjacent space so you could shrink sda3 which looks like your windows system partition.  Don't know what all the other partitions are?

---

### Post by Odense on 2017-05-12
> **yancek said:**
> Running chkdsk after modifying a windows partition is to make sure there are no problems with the partition filesystem.  Hopefully, running it returns no errors.

Turning hibernation on/off is usually done in the BIOS on boot and the method varies with manufacturer.  Check your owners manual.  You may also have some option in windows but I don't use it so can't help with that.

Also, I don't see any free space to which you can extend the Ubuntu partition before it.  To increase the size of a partition, you need adjacent space so you could shrink sda3 which looks like your windows system partition.  Don't know what all the other partitions are?

I could boot to Windows 10 after the reduction and I have ran the chkdsk (after reboot) so that should be OK.

I did not turn off hibernation and I HAVE booted on a live-stick and increased the Ubuntu partition (and checked that I can still boot to both Ubuntu and Windows 10).

The other partitions are the partitions the Laptop came with (I have only added the Ubuntu partition). I THINK one is Windows drivers and one is a backup drive.
I don't really want them - but was not encouraged when I previously asked about deleting them ([https://ubuntuforums.org/showthread.php?t=2352690](https://ubuntuforums.org/showthread.php?t=2352690)). Do you have better advice ?

---

