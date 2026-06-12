---
title: "mp3 player partitioning problems"
date: 2007-11-12
forum: General Help
---

### Post by a7RoX on 2007-11-12
hi everybody

i have problems partitioning my mp3 player (which was messed up by me some time ago :-(  )

just want to know if it is normal that 

[HTML] sudo lshw -C disk[/HTML]

gives me this output for my player?

[HTML]
 *-disk

       description: SCSI Disk
       product: MSCN
       vendor: SigmaTel
       physical id: 0.0.0
       bus info: scsi@12:0.0.0
       logical name: /dev/sda
       version: 0100
       serial: 23DEABAA410DC79F
       size: 1941MB
       capabilities: removable
       configuration: ansiversion=4
     *-disc
          physical id: 0
          logical name: /dev/sda
          size: 1941MB
          capabilities: partitioned partitioned:dos
[/HTML]

semms to be kind of doubled?

would be very pleased if someone could help me, because i dont want to buy a new one :-(

patrick


partitioning with fdisk creates following

[HTML]
patrick@patrick:~$ sudo fdisk /dev/sda
[sudo] password for patrick:
Note: sector size is 2048 (not 512)

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the DOS compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): d
Selected partition 1

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.

Error closing file

[/HTML]

---

