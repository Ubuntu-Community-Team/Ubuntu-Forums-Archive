---
title: "Not seeing usb flash drives"
date: 2016-09-21
forum: General Help
---

### Post by tommy2k10 on 2016-09-21
I am running Ubuntu 16.04.

None of my USB flash drives are recognised, nothing in the sidebar, nothing in Disks.
However, when I run Gparted, sda1 is shown (the main disk), and sda5 (which has got a red exclamation mark next to it); this is a branch of sda2.
When I double-click on sda5, GParted says:

Unable to detect file system.  This could be because of the following reasons:
The file system is damaged
The file system is unknown to GParted.
There is no file system available (unformatted)
The device entry for sda5 is missing

Ubuntu found them before (about a month ago), all I have done between then and now is take one of the Hard disks out of the system, and installed Virtualbox (with USB support).  I removed VBox as I thought it might make a difference but it didn't.

Why is it not recognising them?

---

### Post by sudodus on 2016-09-21
Please plug in your USB flash drives and run the following commands in a wide terminal window and post the output within CODE tags in a reply,

```
df -h
lsusb
sudo lsblk -fm
sudo parted -ls
ls -l /media/*
```

---

### Post by tommy2k10 on 2016-09-21
Can't I just take some screenshots?

---

### Post by sudodus on 2016-09-21
Well, it is actually easier to see and comment the results, when copied from the terminal window and pasted into a reply.

Do you know that you can mark 'paint' with the left mouse button and paste with the middle button (or press the wheel)? That way is convenient also for you compared to using screenshots. 

But screenshots will do if you feel awkward with copy and paste from the terminal window.

---

### Post by tommy2k10 on 2016-09-22
```
Filesystem          Size  Used Avail Use% Mounted on
udev                958M     0  958M   0% /dev
tmpfs               195M  6.2M  189M   4% /run
/dev/sda1           228G  154G   63G  72% /
tmpfs               975M  220K  975M   1% /dev/shm
tmpfs               5.0M  4.0K  5.0M   1% /run/lock
tmpfs               975M     0  975M   0% /sys/fs/cgroup
tmpfs               195M   56K  195M   1% /run/user/1000
/home/tom/.Private  228G  154G   63G  72% /home/tom
tom@tom-M61PM-S2:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0d3d:0022 Tangtop Technology Co., Ltd 
Bus 002 Device 002: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
tom@tom-M61PM-S2:~$ sudo lsblk -fm
[sudo] password for tom: 
NAME   FSTYPE LABEL UUID                                 MOUNTPOINT NAME     SIZE OWNER GROUP MODE
fd0                                                                 fd0        4K root  disk  brw-rw----
sda                                                                 sda    232.9G root  disk  brw-rw----
&#9500;&#9472;sda1 ext4         5956dab5-6266-47ab-8b4c-b89452076b8b /          &#9500;&#9472;sda1   231G root  disk  brw-rw----
&#9500;&#9472;sda2                                                              &#9500;&#9472;sda2     1K root  disk  brw-rw----
&#9492;&#9472;sda5                                                              &#9492;&#9472;sda5     2G root  disk  brw-rw----
tom@tom-M61PM-S2:~$ sudo parted -ls
Model: ATA ST3250410AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  248GB  248GB   primary   ext4         boot
 2      248GB   250GB  2078MB  extended
 5      248GB   250GB  2078MB  logical


tom@tom-M61PM-S2:~$ ls -l /media/*
lrwxrwxrwx  1 root root    7 Dec 11  2013 /media/floppy -> floppy0

/media/floppy0:
total 0

/media/tom:
total 8
drwx------ 2 root root 4096 Jan 21  2014 544EDC454EDC2192
drwx------ 2 root root 4096 Feb  5  2014 ACER

/media/usbstick:
total 0


```

---

### Post by sudodus on 2016-09-22
No USB flash drive is seen as a mass storage device (listed by lsblk and parted).

- What about the output of lsusb: Can you identify the Tangtop device (maybe a keyboard or PS/2 adapter)?

```
Bus 002 Device 003: ID 0d3d:0022 Tangtop Technology Co., Ltd
```

- When booted into a live session from a CD/DVD/USB drive (with Lubuntu), can you see the USB flash drives with the same command lines as you used with the installed system)? (There is also the interesting question: does the computer boot from a USB drive?)

---

### Post by tommy2k10 on 2016-09-22
I cannot boot from anything USB; it seems the USB port is not working!
Sorry if I've wasted your time.
Tangtop is the company that make my KVM switch.

---

### Post by sudodus on 2016-09-22
You did not waste my time. I am here trying to help :-)

It is possible that the USB hardware is broken. But I suggest that you make another check or two, just to find out if there is something wrong in your installed system.

If you still have your Lubuntu boot disk (CD or DVD), it is easy to boot into a live session, 'Try Lubuntu', from there use the commands I suggested in post #2 and post the output. Maybe there is some sign of life in the USB system.

If still no luck, you might try with another (very different, I suggest old linux distro), if that linux version can recognize the USB. For example, you can try with Wary Puppy or Tiny Core. They might lack lsblk and parted, but fdisk should be there, so you can try with

```
fdisk -lu   # or

sudo fdisk -lu   # (if not running as root)
```

Try also the newest version of Lubuntu, not yet released, 'Yakkety Yak', from the QA testing tracker: [http://iso.qa.ubuntu.com/qatracker/milestones/360/builds](http://iso.qa.ubuntu.com/qatracker/milestones/360/builds). There are some bugs, but it can run live and be installed, and it does see USB drives.

-o-

If still no luck, I'm afraid that the USB system is broken (or all the USB flash drives, but it is less likely).

---

### Post by tommy2k10 on 2016-09-22
I have lots of them, but there is no CD / DVD drive in the machine, as it broke!  (And I always use an external USB drive, except I can't now!)  I suppose I could buy one and fit it.

---

### Post by tommy2k10 on 2016-09-22
I have got a disability, so I got a friend who works with computers to open the case, and it wasn't connected!!  (Could the connector have fallen out?)

---

### Post by sudodus on 2016-09-22
It happens that internal connections fail. What was not connected (the CD/DVD drive or the USB ports)?

I'm glad you have a friend who can help you :-)

---

### Post by tommy2k10 on 2016-09-23
The USB port!

---

### Post by sudodus on 2016-09-23
So USB is working now :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by tommy2k10 on 2016-09-23
Sorry; yes it is.  Thankyou.  I will mark it as solved

---

