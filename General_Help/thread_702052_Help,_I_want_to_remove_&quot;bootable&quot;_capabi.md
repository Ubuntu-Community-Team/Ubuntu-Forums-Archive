---
title: "Help, I want to remove &quot;bootable&quot; capability from external drive"
date: 2008-02-19
forum: General Help
---

### Post by thumbsoup on 2008-02-19
I have a Western Digital "My Book" external USB hard drive.  Formatted from the factory as FAT32.  It shows up as "bootable" when it is NOT the boot drive, just has some data on the drive.  I can read and write to the external drive. 

Can I get rid of the "bootable" capability, without losing that data?  Or do all external USB drives show up as "bootable"?

I just installed Ubunut 7.10 on a new internal drive. But the external drive was created back when I was using my old Ubuntu computer.  Data is backed up, so I can lose it, but would be a small hassle.     Regardless, how do I make this drive not "bootable"?

Output of "sudo fdisk -l" is below.  The external drive is sdb (both internal and external drives happen to be 320GB)

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001c4fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38156   306488038+  83  Linux
/dev/sda2           38157       38913     6080602+   5  Extended
/dev/sda5           38157       38913     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38912   312560608+   c  W95 FAT32 (LBA


Partial output of "sudo lshw":

*-disk
             description: SCSI Disk
             product: My Book ES
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 012
             serial: 3
             size: 298GB
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4
           *-volume
                description: W95 FAT32 (LBA) partition
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                capacity: 298GB
                capabilities: primary bootable

---

### Post by astrotech226 on 2008-02-19
If you do:

```
sudo fdisk /dev/sdb
a (toggle's bootable flag)
1 (1st partition)
w (write the partition table)
```

This should remove the bootable flag from the partition.  I just tested this on my equipment and the data stayed intact.

---

### Post by thumbsoup on 2008-02-19
Thanks for responding.  I am not sure how to type all that in.  
I tried: 

sudo fdisk /dev/sdb a 1 w

 and got back this reponse:


Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by astrotech226 on 2008-02-19
I'm sorry...  Those are supposed to be on multiple lines.  Here they are again numbered:

1) sudo fdisk /dev/sdb
2) a
3) 1
4) w

This is actually a conversation going on between you and the fdisk program.  Line #2 is the command and Line #3 is the partition number for the previous command.  Line #4 is another command meaning to write the partition table.

---

### Post by thumbsoup on 2008-02-19
Thanks very much, I think I got it to work now.  Drive no longer shows up as bootable, yet data is still there.

BTW, I followed your language on "toggle's bootable flag" in your earlier response and looked that up.  So I found out about the interactive steps for fdisk.

What was weird is that fdisk reported that it couldn't make the change until the next reboot:

Calling ioctl() to re-read partition table. 

WARNING: Re-reading the partition table failed with error 16: Device or resource busy. 
The kernel still uses the old table. 
The new table will be used at the next reboot. 
Syncing disks.

So I rebooted, and the computer never came back up.  Completely dead, screen stayed dark, like the internal drive died.  Scared me silly, made me think I wrote "sda" instead of "sdb".

Turns out that my computer BIOS includes the "Removable Drive" as the second step in the boot priority:  CD first, then Removable Drive, then hard drive.  Maybe because it used to be "bootable", even though an OS wasn't installed there.  Hmm, guess the computer didn't like the change, don't really know though.

I have changed the boot order, so far so good. 

Thanks again.

---

