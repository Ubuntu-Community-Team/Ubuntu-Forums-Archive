---
title: "is 16gb device to small to fit 14.04?"
date: 2017-05-03
forum: General Help
---

### Post by ubto66 on 2017-05-03
ubuntu 14.04 64bit
16gb usb flash stick

It says, that ubuntu 14.04 64bit requires no more than 6gb hdd for installation. I used to be able to install ubuntu 14.04 64bit on a 16gb usb flash stick and also add many programs. 

Now after installation, updating and adding programs, available free space is close to zero.
Gparted says, the usb flash stick is 14gb. In system settings -> details it says 10gb.
Are these values what they ought to be?

Has the size of ubuntu 14.04 64bit after updating increased, such that you cannot run ubuntu 14.04 64bit on a 16gb usb flash stick?

Thank you.

---

### Post by oldfred on 2017-05-03
Did you do an auto install that created a larger swap?
Post this:
sudo parted -l

---

### Post by ubto66 on 2017-05-04
Thank you. System monitor swap not available.

sudo parted -l
```
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   16,1GB  15,8GB  extended
 5      257MB   16,1GB  15,8GB  logical


Error: /dev/mapper/ubuntu--vg-swap_1: unrecognised disk label             

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 11,5GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0,00B  11,5GB  11,5GB  ext4


Error: /dev/mapper/sda5_crypt: unrecognised disk label
```

---

### Post by RobGoss on 2017-05-04
I would not use anything less then 20-GB, Ubuntu OS is growing and so is its resources that means the HD requirements will also need more space

I believe the recommendation for disk space is 20- GB but that may have changed you would have to check

If you are  seriously planning to use Ubuntu as your main desktop then give that HD as much space as you can you'll be glad you did

---

### Post by oldfred on 2017-05-04
Did you then do an encrypted LVM install. And then swap is inside the LVM. Not shown with gparted.
You show 15.8GB in the LVM, but the LVM partitions inside have to be mounted with LVM tools.

I do not know about LVM nor encryption. That is more advanced, if you want to use it.

 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)
[https://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux](https://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)
Manually create
[http://community.linuxmint.com/tutorial/view/2061](http://community.linuxmint.com/tutorial/view/2061)

---

### Post by C.S.Cameron on 2017-05-04
I recall 10.04 would install to 4GB flash drive.

---

### Post by efflandt on 2017-05-06
I just installed 64-bit 16.04 to 16 GB SD card. I don't use any swap and this is what it shows on the installed system for the whole file system:
efflandt@1604-64-16SD:~$ df -h | grep sdb
/dev/sdb1        15G  4.4G  9.8G  31% /

It shows same for SD card plugged into my desktop system:
efflandt@msata512-1610:~$ df -h /media/efflandt/*
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdc1        15G  4.4G  9.8G  31% /media/efflandt/U1604B64SD

There was a time when you could marginally install Ubuntu on 4 GB, but now 8 GB does not leave you much room after installing updates and programs, etc.

Of course it is different for my main desktop drive which is 512 GB mSATA SSD in a SATA adapter with Steam games and things:
efflandt@msata512-1610:~$ df -h /
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       469G  240G  206G  54% /

---

