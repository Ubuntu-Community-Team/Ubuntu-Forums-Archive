---
title: "Can't get passed &quot;installation type&quot; part of installation process."
date: 2018-02-13
forum: General Help
---

### Post by oarm on 2018-02-13
Hello, I apologize in advance if a solution to this particular issue has already been posted elsewhere, but I've yet to find a solution either here or elsewhere that has been of any help.  I'm new to Linux and I'm having problems with the install. Ive followed the necessary steps to install Linux, namely download a flavor and create a bootable USB. I'm able to boot it up but, when I reach the Installation type part of the install process, I am unable to go forward with the install. If I choose install now, I get a " no root system is defined. Please correct this from the partitioning menu." Prompt and anything else I can press at this stage causes the installer to crash. So far I've tried a few different distros (Mint 18.3 "Sarah", Ubuntu 16.04.1, Xubuntu 17.10.1) and USB booters (Rufus, Universal USB, Linux Live) and I run into the same problem. I'm using an XPS 13 9360 Signature Edition, 8gb ram, 64-bit operating system. Thank you.

---

### Post by TheFu on 2018-02-13
Welcome to the forums.

Did you free up 15+G of storage on the HDD for the installation in at least 2 empty partitions?  
Linux isn't a program to be added inside Windows.
If there aren't 2 free partitions and sufficient storage, then Ubuntu can't be installed.  NTFS is NOT allowed.

Can you boot off the flash drive and "Try Ubuntu"?  Then open a terminal and run '**sudo parted -l**' then post that command and output here.  Please.  Use "Adv Reply" when posted the output and use "code tags" - the '#' button so it is readable.

---

### Post by ajgreeny on 2018-02-13
You will also need to make sure you boot the USB as a UEFI device; the USB will possible appear twice in the device list when you press the appropriate keyboard key so choose the one that starts or includes UEFI in the name.

---

### Post by oarm on 2018-02-13
```
Model: General USB Flash Disk (scsi)
Disk /dev/sda: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.6GB  15.6GB  primary  fat32        boot, lba
```

I made 2 15GB+ partitions: 1 that ubuntu was assigned to when i made the usb bootlable and another unallocated one.

---

### Post by oarm on 2018-02-13
the USB doesn&#8217;t appear twice, although the option that does appear has UEFI in front.

---

### Post by ajgreeny on 2018-02-14
Was that the full output from the **sudo parted -l** command as only your USB disk is shown, with no minternal hard disk on which to install the OS.

---

### Post by TheFu on 2018-02-14
> **oarm said:**
> ```
Model: General USB Flash Disk (scsi)
Disk /dev/sda: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.6GB  15.6GB  primary  fat32        boot, lba
```

I made 2 15GB+ partitions: 1 that ubuntu was assigned to when i made the usb bootlable and another unallocated one.

This shows 1 FAT partition, about 16G in size on a 16G flash disk.  There isn't **any** room for anything else to be installed.

I've never tried to install any Linux onto a USB disk outside of making bootable media or "Live Boot" stuff that can't save anything to the same media, so I really don't know if there are special needs for accessing USB on these new-fangled computers that have EFI booting.  USB is always slower than SATA or eSATA due to the difference in commands available and/or bus limitations, IME.  USB storage commands aren't the same as those from the ATA command set.

As for appearing twice, I think aj meant from the BIOS/EFI boot screen, not in a partition table. I could be wrong.

---

### Post by ajgreeny on 2018-02-14
Yes, that's what I meant.

When you boot from the BIOS/EFI screen which you get to normally from a keypress immediately sfter power-on, the system usually shows a list of the connected devices available, both internal and external; a USB disk usually, in my experience, shows two times, one as UEFI, the second (on my system) as a standard ATAPI disk device.

---

### Post by oarm on 2018-02-15
What I posted before was the entire command output and I understood Aj was referring to the BIOS loading screen. I checked my partitions in windows and the largest was configured for NTFS. Do I split this partition and change it's file set to FAT32? And if so, how do I do this within Ubuntu?

---

### Post by TheFu on 2018-02-15
> **oarm said:**
> What I posted before was the entire command output and I understood Aj was referring to the BIOS loading screen. I checked my partitions in windows and the largest was configured for NTFS. Do I split this partition and change it's file set to FAT32? And if so, how do I do this within Ubuntu?

**Don't do anything at this point.**  Your existing setup is at risk if you do.

I've never seen a BIOS screen that looked like an fdisk -l screen before.

We need to gather some information.   Please post the **fdisk -l** output. Use a live-boot USB drive to get it. sudo is probably necessary and please use (adv reply) with # to wrap the  output in "code tags" so it is readable.
OR
you can install **boot-repair** (yes, you can install programs inside a "live-boot" setup) and run the information gather tool inside that one - boot-info. It will make a URL that you can post here (the URL). It will contain more detailed information which might be necessary, so having it sooner than later would probably be helpful. You probably do not want to ask boot-repair to do anything besides gather information.

---

