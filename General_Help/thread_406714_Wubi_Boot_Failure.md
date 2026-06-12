---
title: "Wubi Boot Failure"
date: 2007-04-11
forum: General Help
---

### Post by Dark Legacy on 2007-04-11
```
Loading Ubuntu, please wait...

check root = bootarg cat /proc/cmdline
or missing modules, devices: cat/proc/modules ls /dev

Alert! Does not exist. Dropping to shell!

BusyBox v1.1.3 Built-in shell (ash)

/bin/sh can't access tty; job control mode off.
```

Help. :(

---

### Post by ago on 2007-04-11
What version of wubi are you using?
Can you run

more /tmp/zenigata.log

Is you HD special (raid, firewire, strange fs...)?

---

### Post by Dark Legacy on 2007-04-11
> **ago said:**
> What version of wubi are you using?
Can you run

more /tmp/zenigata.log

Is you HD special (raid, firewire, strange fs...)?

The version of Wubi I am using is the following: [7.04 Beta v3]("http://cutlersoftware.com/ubuntusetup/latest.html")

Yes, I have an nVidia RAID-0 (striping) array using two Hitachi 7200RPM 160GB drives (totalling 300GB and 14k RPM effectively.)

Command has been run - visual diagnostic is presented below:

[[IMG]http://img402.imageshack.us/img402/744/linuxboot002mediumkh0.jpg[/IMG]](http://imageshack.us)

[[IMG]http://img487.imageshack.us/img487/5404/linuxboot003mediumqc0.jpg[/IMG]](http://imageshack.us)

[[IMG]http://img487.imageshack.us/img487/4038/linuxboot004mediumfb9.jpg[/IMG]](http://imageshack.us)

[[IMG]http://img487.imageshack.us/img487/5250/linuxboot005mediumhm5.jpg[/IMG]](http://imageshack.us)

[[IMG]http://img487.imageshack.us/img487/628/linuxboot006mediumzj9.jpg[/IMG]](http://imageshack.us)

[[IMG]http://img487.imageshack.us/img487/898/linuxboot007mediumxa7.jpg[/IMG]](http://imageshack.us)

[[IMG]http://img487.imageshack.us/img487/928/linuxboot008mediumlj1.jpg[/IMG]](http://imageshack.us)

[[IMG]http://img487.imageshack.us/img487/5820/linuxboot019mediumyo6.jpg[/IMG]](http://imageshack.us)

---

### Post by ecology2007 on 2007-04-11
> Yes, I have an nVidia RAID-0 (striping) array using two Hitachi 7200RPM 160GB drives (totalling 300GB and 14k RPM effectively.)

It is the cause of the problem, the module for your disk controller is probably not included and configured for stripped raid. Hence the wubi folder is not found.

How many partitions do you have on that ?
It is weird that grub ( the very 1st stage of the loading process) managed to read it and find wubi folder.

If you have another drive, cut and paste wubi folder to this drive and that should be ok.
Be sure to remove the old one.

---

### Post by ago on 2007-04-11
> **Dark Legacy said:**
> The version of Wubi I am using is the following: [7.04 Beta v3]("http://cutlersoftware.com/ubuntusetup/latest.html")

Yes, I have an nVidia RAID-0 (striping) array using two Hitachi 7200RPM 160GB drives (totalling 300GB and 14k RPM effectively.)

We only have raid1 at the moment, I will add raid0. It will be available in next version.

---

### Post by Dark Legacy on 2007-04-11
> **ago said:**
> We only have raid1 at the moment, I will add raid0. It will be available in next version.

Thank you very much, I appreciate that very much. :biggrin: 

> It is the cause of the problem, the module for your disk controller is probably not included and configured for stripped raid. Hence the wubi folder is not found.

How many partitions do you have on that ?
It is weird that grub ( the very 1st stage of the loading process) managed to read it and find wubi folder.

If you have another drive, cut and paste wubi folder to this drive and that should be ok.
Be sure to remove the old one.

I have four partitions on my 300GB Striped Drive.

Partition 1: System (Contains Windows) - 41.7GB <- This drive contains Wubi.
Partition 2: Games (Guess) - 120.0GB
Partition 3: Development (Pretty obvious) - 75.0GB
Partition 4: Media (Backup drive, all of my software / movies / family photos) - 70.0GB

---

### Post by mwilley on 2007-04-15
Does this mean that I will be able to use wubi with the next release?  I had the exact same problem, except for some slight differences with the zenigata.log.  One difference is that I did not have anything about the "silicon_medley_raid_member"

---

### Post by tableteer on 2008-05-20
On boot-up set the root= option to the device for your root partition in your /etc/fstab entry.
For example, if /etc/fstab is hda5 then, if you are using grub, append root=/dev/hda5 to the end of the kernel line.

-----------------------------------------------
/etc/fstab:
/dev/hda5        /         reiserfs     noatime,notail 0 1
-----------------------------------------------
menu.lst:
kernel /boot/vmlinuz-2.6.24-16-generic ro root=/dev/hda5

---

