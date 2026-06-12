---
title: "Ubuntu doesn't see usb SanDisk"
date: 2013-08-27
forum: General Help
---

### Post by lumaja2 on 2013-08-27
Ubuntu 12.04 LTS Desktop
 Bought new SanDisk Cruzer Blade 4GB USB when connect not seen in Home or any where else and no error.,
 Tried in another Hard Disk with Ubuntu 10.04 LTS the same, tried at store that I bought with Windows 7 and 8 it works.
 Please let me know what to do connect this USB.

---

### Post by sudodus on 2013-08-27
I have SanDisk Cruzer Blade 4GB USB pendrives, and they work for me

1. as mass storage devices out of the box (as delivered with one partition and fat32 file system)

2. as boot drives, when made into boot drives with several methods, see [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

These USB drives have been reliable for me, but rather slow compared to Sandisk Extreme USB 3 pendrives, 5 MB/s writing speed of big files.

The hardware must be good, since you can use it in Windows. So I suspect it has a partition table or file system not compatible with linux, maybe Microsoft's ***exFAT*** file system. It is possible that Sandisk has started to deliver them like that now (my SanDisk Cruzer Blades are maybe one year old). 

Try if the drive is recognized at all with some terminal window **[COLOR=#0000cd]commands in blue[/COLOR]**

```
**[COLOR=#000080]lsusb[/COLOR]**   
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 0781:5567 SanDisk Corp. Cruzer Blade

```

```
**[COLOR=#0000cd]sudo parted -l[/COLOR]**
[sudo] password for sudodus: 

... (other devices)

Model: SanDisk Cruzer Blade (scsi)
Disk /dev/sdd: 4005MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  1579MB  1578MB  primary  ext2
 2      1579MB  1999MB  419MB   primary  linux-swap(v1)

```

```
**[COLOR=#000080] sudo fdisk -lu[/COLOR]**

... (other devices)

Disk /dev/sdd: 4004 MB, 4004511744 bytes
124 heads, 62 sectors/track, 1017 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bec46

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048     3084287     1541120   83  Linux
/dev/sdd2         3084288     3903487      409600   82  Linux swap / Solaris

```

If the pendrive is recognized as a 'disk', you can try to re-partition and re-format it with gparted

```
gksudo gparted
``` Install gparted if not available
```
sudo apt-get install gparted
```

---

### Post by lumaja2 on 2013-08-27
ent to the store and format the USB to NTFS connect at home still not recognized Tried your idea with “lsusb” with Terminal normal colour the result:  @-G41M-Combo:~$ lsusb Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 005 Device 002: ID 046d:082b Logitech, Inc.  Bus 001 Device 003: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub Bus 001 Device 004: ID 04f3:0103 Elan Microelectronics Corp.  @-G41M-Combo:~$  How do you get the command in blue? I see on the web that it works with Ubuntu and My OS is updated every time an update comes up

---

### Post by sudodus on 2013-08-27
Please post the output between code tags like this
 
[noparse]```
output
```[/noparse]
 
to get output like this
 
```
output
```

It makes it much easier to read :-)

> **lumaja2 said:**
> ent to the store and format the USB to NTFS connect at home still not recognized Tried your idea with “lsusb” with Terminal normal colour the result: ```
 @-G41M-Combo:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:082b Logitech, Inc.
Bus 001 Device 003: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 004: ID 04f3:0103 Elan Microelectronics Corp.
@-G41M-Combo:~$
```
How do you get the command in blue? I see on the web that it works with Ubuntu and My OS is updated every time an update comes up

I have Ubuntu 12.04 LTS too. And I can see and use my pendrives of the same kind. It seems you cannot see the Sandisk Cruzer Blade device at all with Ubuntu 12.04 LTS. What do you mean by the following statement?

> Tried in another Hard Disk with Ubuntu 10.04 LTS the same

Maybe there is something wrong with the computer, the USB system or that particular USB port. Try rebooting, and test all the USB ports.

---

### Post by jlh68 on 2013-08-27
Change the San Disk to a USB mass storage device.  The below is from the SanDisk manual

> If your player does not connect:
1.Unplug the player
2.Select Settings
3.Select System Settings
4.Select USB Mode
5.Change the USB Mode from Auto Detect to MSC
6.Plug your player back into your PC

---

### Post by lumaja2 on 2013-08-28
To sudodus  ```
output
``` I know what you mean but don't understand, tried few ways but nothing come correct. Please explain how I should read and process. The other disk is a smaller HD (80GB) with Ubuntu 10.04 LTS which I connect to My computer to Check the SanDisk. Have 3 other pendrives 1 TDK, 2 ADATA, TRANSCEND their all work properly on both front ports.  To jlh68  In System Settings there ins't USB Mode. Thank you to tried your best to help.

---

### Post by sudodus on 2013-08-28
0. Click [COLOR=#ff0000][SIZE=3]**go advanced**[/SIZE][/COLOR]

1. Please post the output between code tags like this (write the code tags manually or mark the text and use the # icon at the top of the editing window). It makes it much easier to read :smile:

2. Mark the text and select the **A[COLOR=#ff0000]v[/COLOR]** icon at the top of the editing window to change colour.

> **lumaja2 said:**
> ent to the store and format the USB to NTFS  connect at home still not recognized Tried your idea with “lsusb” with  Terminal normal colour the result: ```
 @-G41M-Combo:~$ lsusb
...
Bus 005 Device 002: ID 046d:082b Logitech, Inc.
Bus 001 Device 003: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 004: ID 04f3:0103 Elan Microelectronics Corp.
@-G41M-Combo:~$
```
How do you get the [COLOR=#0000cd]command in blue[/COLOR]? I see on the web that it works with  Ubuntu and My OS is updated every time an update comes up

See the attached file (picture during the editing process)

---

### Post by sudodus on 2013-08-28
Since your other pendrives work in this computer, but not Sandisk Cruzer Blade, there must be something new or special with that pendrive.

Unfortunately the USB systems are subject to variations, and often new versions or batches from production are only tested with the commercial operating systems, Windows and MacOS. Often the hardware will work also with Linux, but not always. You had bad luck and got a Sandisk Cruzer Blade that does not cooperate with the combination of your computer hardware and operating system, although that particular brand name, model and size (4GB) works for many other people [COLOR=#696969](including me; I bought a ten-pack of them and they all work as they should in the same Ubuntu 12.04 LTS version, they are reliable but slow).[/COLOR]

---

