---
title: "Can't install OS's on Asus EEE PC 4"
date: 2012-12-13
forum: General Help
---

### Post by Sally666 on 2012-12-13
Hello,

I have an ASUS eee pc 4g.  It had unbuntu on it running but it was really slow.  I assume it was a netbook version.  I tried to install the following OS' 

LinuxMint 14.1 mate
eeebuntu 3.0 standard
ubuntu 9.10 desktop i386
ubuntu 11.10 desktop i386


on it using unetbootin-windows-442.exe and it just not working.  I'm using a Toshiba flash drive with 15 gb on it.  I've formatted this stick over and over to fat32.  I'm using Win 7 to run unetbootin.  When I first tried LinuxMint it got 1/2 way through the installation and then crashed.  Ever since then, it has not booted to anything with unetbootin.


Any ideas?

Thanks

---

### Post by bcschmerker on 2012-12-13
After reviewing the [specifications for the Eee™ PC 701 4G]("http://www.asus.com/Eee/Eee_PC/Eee_PC_4G"), I found it equipped with the Intel® Celeron™ M 353 and 910 chipset, Ethernet, WLAN, and 4 GB SSD.  I consider 8 GB the minimum secondary storage for any LinUX GUI, as even XFCE contains several server binaries and dozens of library sockets.  According to ASUSTeK, the Eee PC 701 can run Microsoft® Windows® XP™ Home, or alternately GNU® LinUX® 2.6; the design dates back to 2007 and the 701 8G may have been able to run XUbuntu® 8.04-LTS.

---

### Post by mastablasta on 2012-12-13
if it has 4GB drive - that is not enough for Ubuntu. Ubuntu needs more than 4GB probably at least abotu 8 GB hard disk space.
 
however this shouldn't stop it from booting from USB.
 
I suggest you post the exact specificaitons. as for your hard disk size you might give Bodhi Linux a try. Not sure how much space Lubuntu needs, but maybe it would work. otherwise go minimal install iso and then only install things you need. you might be able to squeeze it on 4GB disk.

---

### Post by Pjotr123 on 2012-12-13
Install Lubuntu (low disk space requirements) with EXT2 partitioning. Old SSD.... Tweak your SSD right:
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by Sally666 on 2012-12-13
Wow!

Thanks for the replies!

This is helpful.

These are these are the stats on the machine.

[Asus eee pc 4g]("http://www.asus.com/Eee/Eee_PC/Eee_PC_4G/")

Also, what about tying Damn Small Linux?

---

### Post by Sally666 on 2012-12-16
Still having issues.  I tried to edit the BIOS for SSD, but is a very limited bios that doesn't have the access I need. 

Meanwhile, I tried to use unebootin to load Lubuntu and same issue.

I'm given an  initramfs prompt.  When I type "exit" it freezes.

Any ideas?

---

### Post by Sally666 on 2012-12-16
Found that the issue was UneBootin so now I'm using [PenDrive Linux]("http://www.pendrivelinux.com/") and that loads the OS via USB.

Thanks for helping me!

---

### Post by Statia on 2012-12-16
> **Pjotr123 said:**
> Install Lubuntu (low disk space requirements) with EXT2 partitioning. Old SSD.... Tweak your SSD right:
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)


I can confirm that Lubuntu runs well on the EEE PC 701.
All the hardware is supported and works out of the box: wireless, Ethernet, webcam, touchpad, function keys.

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       2.3G  1.7G  487M  78% /
udev            237M  4.0K  237M   1% /dev
tmpfs           245M     0  245M   0% /tmp
tmpfs            98M  396K   98M   1% /run
none            5.0M  4.0K  5.0M   1% /run/lock
none            245M     0  245M   0% /run/shm
none            100M     0  100M   0% /run/user
tmpfs           245M     0  245M   0% /var/spool
tmpfs           245M     0  245M   0% /var/tmp
/dev/sdc1       597G  280G  317G  47% /media/backup
/dev/sda4       916M   38M  832M   5% /home
```I gave it a 2.3G root partition. With a default install, this barely fits. I removed a lot of GUI programs, since it is living in a box together with an external HDD to be my NAS.
I also gave it 512MB swap, you probably could use half that and not have a separate home partition like I have.

It is nice to breathe new life in to old hardware with distributions like Lubuntu!

---

### Post by bcschmerker on 2012-12-17
> **Statia said:**
> I can confirm that Lubuntu runs well on the EEE PC 701.
All the hardware is supported and works out of the box: wireless, Ethernet, webcam, touchpad, function keys.

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       2.3G  1.7G  487M  78% /
udev            237M  4.0K  237M   1% /dev
tmpfs           245M     0  245M   0% /tmp
tmpfs            98M  396K   98M   1% /run
none            5.0M  4.0K  5.0M   1% /run/lock
none            245M     0  245M   0% /run/shm
none            100M     0  100M   0% /run/user
tmpfs           245M     0  245M   0% /var/spool
tmpfs           245M     0  245M   0% /var/tmp
/dev/sdc1       597G  280G  317G  47% /media/backup
/dev/sda4       916M   38M  832M   5% /home
```I gave it a 2.3G root partition. With a default install, this barely fits. I removed a lot of GUI programs, since it is living in a box together with an external HDD to be my NAS....

It is nice to breathe new life in to old hardware with distributions like Lubuntu!
Thanks for a confirmation on LUbuntu®.  I'll definitely consider this sub-distro for older desktop hardware that can run efficiently in a non-GUI environment with any number of hard drives.

---

