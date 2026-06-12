---
title: "Want to remove GRUB from external hard drive leaving partitions in tact"
date: 2007-12-15
forum: General Help
---

### Post by alfredska on 2007-12-15
I moved what used to be an internal drive in a desktop to an external enclosure which I use with my notebook.  I no longer have a desktop.  I originally had Ubuntu installed to the drive, and let it write a boot sector to the MBR.  I have since deleted all of the partitions and created new storage partitions.  There are three paritions on the drive, in order: 40GB FAT32, 500GB NTFS, 120GB EXT3. They are all storage volumes, no OS.

**I would like to erase only GRUB's boot information from the MBR while keeping the partitions intact.**

Right now, if I try to boot from USB, this drive is seen and GRUB tries to load. GRUB then fails since there is no longer an OS on this drive.  If I tell the computer to boot from USB, I would like the computer to skip over this drive, rather then trying to boot it.

I have both Ubuntu Gutsy and Vista up and running and can use tools for either OS.  I do not have a floppy drive so tools which boot from a DOS floppy are difficult for me to create (seeing as they need to access USB).

These are the web pages I'm referencing right now, and it seems that I should be able to simply change a byte on the first sector to say: non-bootable, but I'm not sure exactly how to go about doing this.
[http://wapedia.mobi/en/Master_boot_record](http://wapedia.mobi/en/Master_boot_record)
[http://mirror.href.com/thestarman/asm/mbr/GRUB.htm](http://mirror.href.com/thestarman/asm/mbr/GRUB.htm)
[http://mirror.href.com/thestarman/asm/mbr/BootToolsRefs.htm](http://mirror.href.com/thestarman/asm/mbr/BootToolsRefs.htm)
[http://en.wikipedia.org/wiki/Master_Boot_Record](http://en.wikipedia.org/wiki/Master_Boot_Record)

Can you help me either remove all traces of GRUB from the MBR, or at least set the drive to non-bootable?

Here's a screenshot of gparted and the first sector of my HD:
[IMG]http://bengal.missouri.edu/mdmnq5/comp/gparted.jpg[/IMG]

[IMG]http://bengal.missouri.edu/mdmnq5/comp/sec01.png[/IMG]

Thank you,
Matt

---

### Post by alfredska on 2007-12-15
I may have found my own answer:

According to [http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/](http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/) I should be able to issue the following command:```
# dd if=/dev/null of=/dev/sdX bs=446 count=1
```replacing X with my device number.

I'll back-up my MBR, give this a go, and report.

---

### Post by alfredska on 2007-12-15
This almost works.

While using dd to zero out the first 446 bytes of my MBR did effectively prevent GRUB from loading and kept my partition table in-tact, I haven't reached my ultimate goal.  I was hoping for my BIOS to skip past this USB device and look for the next available bootable USB device.  Unfortunately, now the computer just hangs after trying to access my external hard drive, without any messages.

I have a USB stick that is bootable, and as long as this external HD is plugged in, the computer can't see past it.  Is this something I won't be able to surmount?  A BIOS issue?

Dell Inspiron 1520

---

### Post by logos34 on 2007-12-15
So you can't change the bios boot order of the usb drives?  Mine show up as 'USB-HDD' in the same place as the hard disks.  You might poke around in the bios for a way to 'disable' the usb drive as a boot device...some bios's allow you to do that--I know my intel machine has a setting like that.  Maybe try a different usb port?  just a guess.  interesting question.

---

### Post by alfredska on 2007-12-15
My BIOS allows me to select which devices I would like to have it boot at startup, so yes I do disable USB for normal routine.  My problem is when I WANT to boot from a USB device, I can't have this external hard drive connected.  Yet, I NEED it connected, so that the BIOS sets it up and I can use it in GHOST.

I tried the LILO method of installing a dummy config to the boot sector and subsequently uninstalling it:
```
lilo -M /dev/sdb -b /dev/shd
lilo -U -M /dev/sdb -b /dev/sdb
```

Again the partitions are fine.  Now at boot, I receive a message about no bootable partitions, then the BIOS jumps to my computer's first drive and boots like normal.

I can't seem to get the computer to recognize any other USB boot devices other than this darned external hard drive.

---

### Post by logos34 on 2007-12-15
The device boot order menu (removable, cdrom, hard drive) is separate from the hard disk boot order.  Don't you have the latter, where you can choose the **hard disk** priority--i.e. rearrange the order so the usb flash drive comes before the usb hard disk?

---

### Post by alfredska on 2007-12-15
That is the option that I do not have.  While I have a device order option (Hard Drive, USB, Network, CD-ROM), I do not have USB device options (USB Thumb, USB Hard Drive, USB Other).

Thus, I can't tell the computer which USB device I'm interested in.

Dell Inspiron 1520

---

### Post by alfredska on 2007-12-15
Ok, so new route.  I do have GRUB installed on my laptop.  Can have it detect which USB devices are connected and boot one from there?

---

### Post by logos34 on 2007-12-15
you should be able to simply add it to menu.lst and select it there at boot. (but the location of the flash drive will change if you unplug the other usb.  But you can simply change one number at startup, so no big deal)

post

**sudo fdisk -l**

---

### Post by alfredska on 2007-12-15
Indeed, I think this is going to do it:
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

Like you mentioned, the only problem with this is if the device number changes.

---

### Post by logos34 on 2007-12-15
That page is for when your bios does not support usb boot.  That's not your problem.

With the other usb plugged in the bios address of the flash drive is (hd2)--i.e the third hard disk. When the other usb is disconnected it will become the second drive in the system, or (hd1).

So if you had a bootable linux on the first partition of that drive, you would have to hit 'e' key and change the 'root' from (hd2,0) to (hd1,0).  Or just have two entries with both locations and select the appropriate one depending on whether the other usb is connected or not.  There may be an easier way I'm unware of, though.

What is on the flash drive?

---

### Post by alfredska on 2007-12-16
Ghost is on the flash drive.  MS-DOS (version from Win98) as it's OS.

I couldn't seem to make this method work.  My flash drive is connected as /dev/sdc when Ubuntu is booted up, but using entry (hd2,0) for grub didn't work (no device found).

My GRUB menu.lst entry reads as follows:

title USB
root (hd2,0)
makeactive
chainloader +1

This is of course with both the external HD and flash drive connected (as I need both of them available for ghost, one to boot from and one to backup to)

---

### Post by logos34 on 2007-12-16
again, could you post 

sudo fdisk -l

To verify how bios sees drives:

sudo grub

> geometry (hd2)

---

### Post by alfredska on 2007-12-16
With pleasure: fdisk -l
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        9536    76549725    7  HPFS/NTFS
/dev/sda3            9537       14593    40620352+   f  W95 Ext'd (LBA)
/dev/sda5           14332       14593     2104483+  dd  Unknown
/dev/sda6            9537       14083    36523714+  83  Linux
/dev/sda7           14084       14331     1992028+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22900a09

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5349    42965811    b  W95 FAT32
/dev/sdb2            5350       70620   524289307+   7  HPFS/NTFS
/dev/sdb3           70621       91201   165316882+  83  Linux

Disk /dev/sdc: 521 MB, 521142272 bytes
255 heads, 63 sectors/track, 63 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x243bfb4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          63      506016    6  FAT16
```

and: geometry (hd2)
```
geometry (hd2)
drive 0x82: C/H/S = 63/255/63, The number of sectors = 1017856, /dev/sdc
   Partition num: 0,  Filesystem type is fat, partition type 0x6
```

Notice the flash drive is /dev/sdc

---

### Post by logos34 on 2007-12-16
sdc is indeed (hd2).

umm...maybe the chainloader grub entry is the problem:

> title USB
root (hd2,0)
makeactive
chainloader +1

dunno.  out of ideas.  There's the [configfile]("http://www.users.bigpond.net.au/hermanzone/p15.htm#1._Configfile") format also.  But I don't know what you'd point it to in ghost (i.e. menu.lst equivalent)  *or that might not work since it doesn't also use grub

---

### Post by alfredska on 2007-12-16
According to the article you sent me, it looks like I should be targeting the mbr of the flash drive (hd2) instead of (hd2,0).  Let me give that a whirl.

UPDATE: Nope, still receiving:```
Error 21: Selected disk does not exist...
```

---

### Post by alfredska on 2007-12-16
New attempt: 

Updated /boot/grub/device.map file to include
```
(hd2)   /dev/sdc
```
whereas before it only contained lines for (hd0) and (hd1)

I then ran:
```
sudo grub
root (hd0,5)
setup (hd0,5)
quit
```

Status: Still can't boot from USB... and running out of ideas.  Perhaps I'll look into that config file mentioned.

---

