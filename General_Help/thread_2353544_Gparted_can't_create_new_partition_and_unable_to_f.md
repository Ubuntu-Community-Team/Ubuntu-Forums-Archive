---
title: "Gparted can't create new partition and unable to force umount"
date: 2017-02-22
forum: General Help
---

### Post by Romein on 2017-02-22
Hi All,

I have some pc troubles and trying to use gparted to fix. In fdisk i accidently removed Ubuntu partition. Tried fresh install but partition table is empty and unable to install. Trying to create new partition now using gparted but unable to cuz it's greyed out. Also unable to unmount. 

I want to add partitions to the hdd to be able to install fresh Ubuntu installation but now i can't even use the "try before installing ubuntu" anymore. It just shows black screen and promt to insert media and press ant key. Can only get in gparted now but almost everuthing greyed out and when i force umount it says busy. Can any you help with this?

Romy

---

### Post by bearlake on 2017-02-22
*** Backup any data first before making any changes ***

Install gparted to a USB and boot live from the USB.

Then select the drive and make your changes from there.

---

### Post by Romein on 2017-02-23
Thanks Bearlake,

I'm on live boot from USB now and confused. I am able to create a new partition now but the partition size is only like 7gb. 

[http://imgur.com/00CNwNg](http://imgur.com/00CNwNg)

 Also checked testdisk to restore partition but it only finds my USB as fat32. I think i need to recreate partition table and restore master boot but how do i go about doing that?

---

### Post by Romein on 2017-02-23
Hi All,

My hdd is a mess and i need to reacreate the partition table to restore master boot.

 I am now in live boot via USB and have used Gparted and testdisk but they list my usb drive i think.

```

Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 7761 MB / 7401 MiB - CHS 1022 239 62
     Partition               Start        End    Size in sectors
>  EFI System                    40     409639     409600 [EFI]
   EFI System                    46     409645     409600 [EFI]
   MS Data                    38294      44291       5998 [GParted-EFI]
   MS Data                   411648   15157247   14745600 [CHELLA]
   MS Data                   411654   15157253   14745600 [CHELLA]
   MS Data                   445320     452701       7382 [OCS-EFI]
   MS Data                  8056982    8059861       2880 [EFISECTOR]
   MS Data                  8059862    8062741       2880 [EFISECTOR]
   MS Data                 10329194   10335191       5998 [GParted-EFI]
   MS Data                 10888310   10894307       5998 [GParted-EFI]


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
                P=Primary  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
root@partedmagic:~# ^C209 MB / 200 MiB
root@partedmagic:~# 

```

Gparted only shows 7,23 GiB as unallocated:

[http://imgur.com/00CNwNg](http://imgur.com/00CNwNg)

How can i fix this? I know it must be to recreate the partition tables because when i insert Windows or Ubuntu installation disk it shows no drives to be installed on. Have also tried inserting the drivers & utillities disk when trying to install windows but no partition shows after it's done.

---

### Post by Romein on 2017-02-23
Ok, i think i found something that might be causing it.

After checking gdisk this is what i get:

```

root@partedmagic:~# gdisk
GPT fdisk (gdisk) version 0.8.6

Type device filename, or press <Enter> to exit: gdisk /dev/sda
Problem opening gdisk /dev/sda for reading! Error is 2.
The specified file does not exist!
root@partedmagic:~# gdisk /dev/sda1
GPT fdisk (gdisk) version 0.8.6

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by typing 'q' if
you don't want to convert your MBR partitions to GPT format!
***************************************************************

```

The GPT is not present and i think that's why it only shows 7,23 GiB. Am i correct?

How do i go about creating a new GPT partition table and allocate the missing space back and reacreate partition tables? It's like 500Gb missing now.

---

### Post by Romein on 2017-02-23
Ok, just created a new GPT partition table and this is what it looks like:

```

root@partedmagic:~# fdisk /dev/sda
Welcome to fdisk (util-linux 2.23.2).

Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.


Command (m for help): g
Building a new GPT disklabel (GUID: 98DD50AF-BCB7-4A75-A50B-93B43E79959E)


Command (m for help): p

Disk /dev/sda: 7761 MB, 7761035264 bytes, 15158272 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk label type: gpt


#         Start          End    Size  Type            Name

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
root@partedmagic:~# gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.6

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): 

```

The MBR table is protective now and GPT is present.

Where do i go from here?

---

### Post by bearlake on 2017-02-23
Is this a usb stick or hdd?

What are your computer specs?

---

### Post by Romein on 2017-02-23
Still no luck. Disk space is vanished like dust in the wind and testdisk still says no partition is bootable. 
Anyone knows how to fix this and recreate partition tables?

```

Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 7761 MB / 7401 MiB - CHS 1022 239 62
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P EFI GPT                  0   0  2  1022 230 16   15158271

Warning: Bad ending sector (CHS and LBA don't match)
No partition is bootable



```

Also when i put the cylinders to 255 it wont change and just stays at 239:

```

Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 7761 MB / 7401 MiB - CHS 1022 239 62

Warning: the current number of heads per cylinder is 239
but the correct value may be 255.
You can use the Geometry menu to change this value.
It's something to try if
- some partitions are not found by TestDisk
- or the partition table can not be written because partitions overlaps.



```

---

### Post by Romein on 2017-02-23
I'm on parted magic live USB. The HDD gives a black screen when trying to boot normal with: insert bootable disc media ... etc.. press any key..

This happened after i accidentally deleted the partition. Normally testdisk recovers it but now it shows only my USB drive and no other disks/partitions.

```

Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 7761 MB / 7401 MiB - CHS 1022 239 62
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P EFI GPT                  0   0  2  1022 230 16   15158271

Warning: Bad ending sector (CHS and LBA don't match)
No partition is bootable

```

This is what lshw shows:

```

physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 3HD9
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 6
          bus info: usb@1:1
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Cruzer Edge
             vendor: SanDisk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sda
             version: 1.27
             size: 7401MiB (7761MB)
             capabilities: removable
             configuration: ansiversion=6 sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sda
                size: 7401MiB (7761MB)
                capabilities: partitioned partitioned:dos
              *-volume UNCLAIMED
                   description: EFI GPT partition
                   physical id: 1
                   capacity: 7401MiB
                   capabilities: primary nofs


```

lshw -short

```

/0/3/1                      memory      512KiB L2 cache
/0/100                      bridge      RD890 PCI to PCI bridge (external gfx0 port B)
/0/100/2                    bridge      RD890 PCI to PCI bridge (PCI express gpp port B)
/0/100/2/0                  display     Turks PRO [Radeon HD 6570/7570]
/0/100/2/0.1                multimedia  Turks/Whistler HDMI Audio [Radeon HD 6000 Series]
/0/100/9                    bridge      RD890 PCI to PCI bridge (PCI express gpp port H)
/0/100/9/0                  bus         EJ188/EJ198 USB 3.0 Host Controller
/0/100/11                   storage     SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
/0/100/12                   bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/12.2                 bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/100/13                   bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/13.2                 bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/100/14                   bus         SBx00 SMBus Controller
/0/100/14.1                 storage     SB7x0/SB8x0/SB9x0 IDE Controller
/0/100/14.2                 multimedia  SBx00 Azalia (Intel HDA)
/0/100/14.3                 bridge      SB7x0/SB8x0/SB9x0 LPC host controller
/0/100/14.4                 bridge      SBx00 PCI to PCI Bridge
/0/100/14.5                 bus         SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
/0/100/15                   bridge      SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
/0/100/15.3                 bridge      SB900 PCI to PCI bridge (PCIE port 3)
/0/100/15.3/0   eth0        network     RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
/0/100/16                   bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/16.2                 bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/101                      bridge      Family 10h Processor HyperTransport Configuration
/0/102                      bridge      Family 10h Processor Address Map
/0/103                      bridge      Family 10h Processor DRAM Controller
/0/104                      bridge      Family 10h Processor Miscellaneous Control
/0/105                      bridge      Family 10h Processor Link Control
/0/5            scsi1       storage     
/0/5/0.0.0      /dev/cdrom  disk        DVD A  DH16ABLH
/0/6            scsi6       storage     
/0/6/0.0.0      /dev/sda    disk        7761MB Cruzer Edge
/0/6/0.0.0/0    /dev/sda    disk        7761MB 
/0/6/0.0.0/0/1              volume      7401MiB EFI GPT partition


```

This is what df -h shows

```

root@partedmagic:~# sudo df -h
df: cannot read table of mounted file systems: No such file or directory
root@partedmagic:~# 


```

---

### Post by Romein on 2017-02-23
My hdd is something like 500+ Gb but somehow it only shows 7Gb in testdisk and Gparted. I think it's just showing my USB size.

---

### Post by QIII on 2017-02-23
Hello!

What manufacturer and model is the disk?  What is the firmware version?

If you restart and enter your BIOS/UEFI menu, is the disk recognized?

---

### Post by oldfred on 2017-02-23
Is your hard drive only 8GB?
That looks more like flash drive.

And if flash drive is sda, is hard drive then sdb, some systems promote flash drive to sda.
Or they make flash drive sda, as BIOS/UEFI has not seen a drive to report to operating system that drive is there.
Does BIOS see hard drive in installed drive list (not bootable drive list).

What brand/model system.
Is drive in laptop or desktop? 
Best to check connections, make sure not loose.

---

### Post by Bucky Ball on 2017-02-23
> **oldfred said:**
> And if flash drive is sda, is hard drive then sdb, some systems promote flash drive to sda.

... so launch Gparted and hit the drop-down box in the top right-hand corner where it says 'sda' and see if you have an sdb. If so, select it as probably the hard drive. ;)

---

### Post by Romein on 2017-02-23
> **oldfred said:**
> Is your hard drive only 8GB?
That looks more like flash drive.

And if flash drive is sda, is hard drive then sdb, some systems promote flash drive to sda.
Or they make flash drive sda, as BIOS/UEFI has not seen a drive to report to operating system that drive is there.
Does BIOS see hard drive in installed drive list (not bootable drive list).

What brand/model system.
Is drive in laptop or desktop? 
Best to check connections, make sure not loose.

It must be flash drive because the hdd is at least 500gb but i don't knwo where the heck that went. I can't find it in testdisk. Also not /dev/sdb:

```
fdisk: cannot open /dev/sdb: No such file or directory
```

I need to recreate the partition tables and fix the boot sector but all the info i find assumes you have hard drive partitions in place to fix the reboot sector but all i see in testdisk is flash drive 8GB. Also in Gparted i don't see anything else but the flash drive. There is no drop down to choose from at all.

Basically it comes down to recreating partition tables and fix boot sector but all i see now is flash drive, in parted magic aswell in Ubuntu USB boot. When i try to install Ubuntu i see this:

[http://imgur.com/a/u4wEh](http://imgur.com/a/u4wEh)

Something is seriously messed up after i accidentally deleted the partition.

Where do i go from here?

**Edit:** In EUFI i can see the HD there. Also when i click on it in boot menu it just gives the: insert bootable media blablabla and press any key to continue

---

### Post by Romein on 2017-02-23
> **QIII said:**
> Hello!

What manufacturer and model is the disk?  What is the firmware version?

If you restart and enter your BIOS/UEFI menu, is the disk recognized?


Seagate - Barracuda STX 720011
Firmware HP23

Disk is recognized in EUFI but when i click on it in boot menu it's stuck in the black screen: Insert bootable ..... and press any key to continue.

If i try to install Ubuntu i get this:

[http://imgur.com/a/u4wEh](http://imgur.com/a/u4wEh)

Somehow i can't get on the HD drive and am now on the flash drive. How do i fix that?

---

### Post by QIII on 2017-02-23
Threads merged.

---

### Post by QIII on 2017-02-23
What you are probably running into is a known firmware issue with many of those drives:  The drive gets stuck in "busy" mode and becomes a brick.  It's detected by the BIOS/UEFI, but is unusable.

I had one do this several years ago and to fix it I had to fabricate a connector from a USB cable, use a specific pin arrangement and send a number of commands to the drive to un-brick it.

That was with the SD15 firmware, but I see several instances of HPxx firmware when I google.

I'm at work waiting for a test to complete, so I can't do much detailed research, but I would suggest googling

```
Seagate Barracuda STX 720011 busy
```

to see what you can find.

---

### Post by Romein on 2017-02-24
Thanks QIII,

I have contacted Seagate and it's a known problem. I guess that's why testdisk couldn't find anything. There's also no firmware updates for s/n 9vs525svq on the seagate website. 

Would you say that there's no other option than to remove the disk and try to fix or is there a way to fix it without removing?

---

### Post by Romein on 2017-02-24
OK Guys,

This is definitely a hard disk issue. The HDD decided to just show up again when i turned on the PC today. So i went into Gparted and tried to create a new partition table. After clicking swapoff i got this error:

```

Error fsyncing/closing /dev/sda1: Input/output error

```

It's the same when creating new partitions when trying to install Ubuntu.

Does this mean i can throw the hdd away, or is there another way to get it working again?

---

### Post by Bucky Ball on 2017-02-24
What happens in Gparted when you, MAKING SURE YOU ARE ON THE CORRECT DISK in the top-right drop-down box, go to the Device menu> Create new partition table?

Be warned that if successful this will clobber any and all data you have on that drive and obliterate the current partition table. Last resort.

---

### Post by Romein on 2017-02-25
In partedmagic i managed to create a new partition table. On the Ubuntu live cd i kept getting the error message fsync...

This is what disk health says:

[URL="http://imgur.com/RHGZtTu"]http://imgur.com/RHGZtTu

[/URL]Basically it says Overall Health Self-Assessment Test: FAILED

I will try how far this disk can go but not sure now how to edit Fstab the correct way. This is what i see:

```

/dev/sda1 /media/sda1 auto defaults 0 0
/dev/sda2 /media/sda2 auto defaults 0 0
/dev/sda3 /media/sda3 auto defaults 0 0
/dev/sda4 /media/sda4 auto defaults 0 0

```

I think i have to edit the media part to correct mount point. Am i correct?

---

### Post by Bucky Ball on 2017-02-26
> **Romein said:**
> I think i have to edit the media part to correct mount point. Am i correct?

Well, the mountpoint you are trying to mount the partition to needs to exist for a start. For instance:

```
/dev/sda4 **_/media/sda4_** auto defaults 0 0
```

Does the mountpoint '/media/sda4' exist on your install??? Or anywhere? You are trying to mount the partition '/dev/sda4/' to it, so it should.

---

### Post by Romein on 2017-03-03
HDD is dead.

Thank you all for trying to help.
I tried everything to revive the disk, even got Ubuntu installed again but the disk has multiple bad sectors, I/O and FDPMA errors.

Do you guys think this one is any good:

[https://www.enter247.nl/shop/index.php?dispatch=products.view&product_id=1741](https://www.enter247.nl/shop/index.php?dispatch=products.view&product_id=1741)

---

### Post by bearlake on 2017-03-03
> **Romein said:**
> HDD is dead.

Thank you all for trying to help.
I tried everything to revive the disk, even got Ubuntu installed again but the disk has multiple bad sectors, I/O and FDPMA errors.

Do you guys think this one is any good:

[https://www.enter247.nl/shop/index.php?dispatch=products.view&product_id=1741](https://www.enter247.nl/shop/index.php?dispatch=products.view&product_id=1741)

Looks good.

Have you thought of an SSD?

Great way to bring new life into your computer.

---

### Post by Bucky Ball on 2017-03-04
Please mark the thread as solved to help others as you've discovered you have a dead disk and gotten to the bottom of your issue. Thread Tools at top right of page. Doing this will not close the thread, just save people some time. 

Good luck. ;)

---

