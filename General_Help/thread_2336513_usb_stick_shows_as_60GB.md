---
title: "usb stick shows as 60GB"
date: 2016-09-09
forum: General Help
---

### Post by pedro_rodriguez2 on 2016-09-09
I have 2 usb sticks, 1 8GB, 1 16GB. 1 is a Ubuntu 16.04 boot usb stick, the other is a Fedora 23 boot usb stick. I want them back to use as a normal usb stick. When I start gparted, it says 'partition is 2024 Linux says it is 512'

I cannot reformat these to fat32 or anything.

What can I do? Please see attached screenshot.

---

### Post by Dennis N on 2016-09-09
First create a new partition table. From gparted, Devices > Create Partition Table. After that, create your partitions by selecting the unallocated space, and use Partition > New.

---

### Post by carl4926 on 2016-09-09
Where X = your USB device

# umount /dev/sdX
# dd if=/dev/zero of=/dev/sdX count=100
[COLOR=#000000][FONT=&quot]That destroys the boot sector, partition table, and initial structures. Any operating system should be happy to reformat it again.[/FONT][/COLOR]

---

### Post by pedro_rodriguez2 on 2016-09-09
I think this is another 16.04 issue. I started 14.04 and got the Toschiba stick back, formatted it fat32. Why did it show a 16GB stick as nearly 60GB? Damn Startup disk creator! 

> pedro@pedro-275E4E-275E5E:~$ sudo dd if=/dev/zero of=/dev/sdb count=100
100+0 records in
100+0 records out
51200 bytes (51 kB, 50 KiB) copied, 0.0111432 s, 4.6 MB/s
pedro@pedro-275E4E-275E5E:~$ 


The above did the trick! I thought it would take a long time, but it just took a fraction of a second!

---

### Post by sudodus on 2016-09-09
Don't blame the Ubuntu Startup Disk Creator. There is finally a ***robust*** version, 0.3 (0.3.2 and 0.3.3), in Ubuntu 16.04 and 16.04.1 LTS.This version ***clones*** the iso file (instead of fiddling with the internal structure of the iso file and getting problems, when that structure is changed between versions of Ubuntu).

The file system comes with the iso file. It is an iso 9660 file system, and there are some special tweaks at the head end of the iso file (and drive), to make it able to boot (as cloned) both in a DVD drive and a USB drive (actually any mass storage device, for example a hard disk drive and a memory card, for example SD or microSD). With the special tweaks, the iso file is called a ***hybrid*** iso file.

Unfortunately gparted does not recognize all pendrives cloned from isohybrid iso files. But they work to boot computers.

If you want a GUI program to manage to wipe 'confusing' data from the pendrive and at the same time create a standard partition table and file system, you can use mkusb according to this link:

[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

The main purpose of mkusb is to*** wrap a safely belt around dd*** when making USB boot drives. dd is a very powerful but also dangerous tool. It does not ask any questions, so if you tell it to wipe your family pictures, it will do that without warnings and double-checking. And it is as easy as getting a single letter wrong in the command line. 'Disk Destroyer' and 'Data Destroyer' are two nick-names for dd ;-)

mkusb can also make some tasks more convenient. Restoring pendrives after using them as boot drives is one of those tasks.

---

### Post by pedro_rodriguez2 on 2016-09-09
Thanks for that, I'll check it out, but as far as I am concerned, 16.04 is not mature, I keep getting problems. Maybe next year it will get better. I pay for my Ubuntu, so I would like it to work without quite so many hitches!

---

