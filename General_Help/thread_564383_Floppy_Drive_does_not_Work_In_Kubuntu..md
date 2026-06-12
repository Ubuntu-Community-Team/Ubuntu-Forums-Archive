---
title: "Floppy Drive does not Work In Kubuntu."
date: 2007-10-01
forum: General Help
---

### Post by Pepse3 on 2007-10-01
Well, after looking at a couple other posts I see there is no follow up that answers the problem.   I am running Kubuntu 7.04.  When I go to System Menu-Storage Media and click on the "floppy0" the LED on the floppy lites up for about 2 seconds and then nothing.  Opened a Konsole and did "cd /media/floppy0 " and it went there.  Did "ls" and nothing happened.  On one of the posts it mentions opening a Konsole (terminal) and entering " sudo mount /dev/fd0 /media/floppy0 " and  " dmesg | grep -i floppy " . Here are my answers to those:  jim@jims-computer:~$ sudo mount /dev/fd0 /media/floppy0
Password:
jim@jims-computer:~$ dmesg | grep -i floppy
[   26.187963] Floppy drive(s): fd0 is 1.44M
jim@jims-computer:~$ sudo mount /dev/fd0 /media/floppy0
Password:
mount: block device /dev/fd0 is write-protected, mounting read-only
mount: /dev/fd0 already mounted or /media/floppy0 busy
mount: according to mtab, /dev/fd0 is already mounted on /media/floppy0
jim@jims-computer:~$
  I never had any problems with other Linux OS'es, why Kubuntu?  Also, I tried to mount the floppy in WINE and it doesn't work there either.

Later. Pepse.

---

### Post by distroman on 2007-10-01
Could you post the following output?
```
cat /etc/fstab
```

---

### Post by Pepse3 on 2007-10-02
jim@jims-computer:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cf3e99f8-e2d1-470d-9f7c-087bc179e2b7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=fbffd057-d2d0-41c0-b97b-7a9fa51a3c1e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
jim@jims-computer:~$

Later. Pepse.

---

### Post by lkraemer on 2007-10-03
I have the exact same problem in Ubuntu 7.04 (INSTALLED) and the LIVECD doesn't work either.

Here is my data:

Can Not Mount Floppy Drive in Ubuntu 7.04 or from LIVE CD.  Knoppix 5.1.1 Live CD
does not work either.  Kubuntu LiveCd doesn't work either.  Fedora 6.02 LiveCD Doesn't work eiter. 

Floppy Drive and 3.5" Disk are good, and work in other
computers.  Floppy will boot to Win98SE Install with a Win98SE
Install Floppy inserted.  Win2K will read the floppy with text
files that Ubuntu won't Mount/Access.

Partial output of DMESG follows:

[   17.149150] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   17.149475] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[   17.149484] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
[   17.149495] VP_IDE: chipset revision 6
[   17.149498] VP_IDE: not 100% native mode: will probe irqs later
[   17.149509] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   17.149517]     ide0: BM-DMA at 0xe600-0xe607, BIOS settings: hda:pio, hdb:pio
[   17.149529]     ide1: BM-DMA at 0xe608-0xe60f, BIOS settings: hdc:pio, hdd:pio
[   17.149536] Probing IDE interface ide0...
[   17.171663] usbcore: registered new interface driver usbfs
[   17.171684] usbcore: registered new interface driver hub
[   17.171704] usbcore: registered new device driver usb
[   17.172558] USB Universal Host Controller Interface driver v3.0
[   17.248582] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
[   17.390471] Floppy drive(s): fd0 is 1.44M
[   17.430389] FDC 0 is a post-1991 82077
[   17.617723] hda: Hitachi HDT725025VLAT80, ATA DISK drive
[   18.288973] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   18.300210] Probing IDE interface ide1...
[   19.442944] hdd: LITE-ON DVDRW LH-20A1P, ATAPI CD/DVD-ROM drive
[   19.499460] ide1 at 0x170-0x177,0x376 on irq 15
[   19.512895] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[   19.512904] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17


Contents of /ETC/FSTAB follows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=b819fb61-9025-4ce6-b451-59cc2c86e55d /               ext3    defaults,errors=remount-ro $
# /dev/hda5
UUID=36648f2f-8907-4fcc-b809-73254e2bf032 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Folder located at:
/media/floppy0
which should be the mount point.


Error when trying to Mount Floppy is:

CANNOT MOUNT VOLUME
Unable to mount Volume

Details
Mount: I could not determine the filesystem type, and none was specified.


root@lkraemer-desktop:/# ls -la /mnt
total 8
drwxr-xr-x  2 root root 4096 2007-10-10 20:55 .
drwxr-xr-x 21 root root 4096 2007-10-04 06:55 ..

root@lkraemer-desktop:/# ls -l /dev/fd0
brw-rw---- 1 root floppy 2, 0 2007-10-12 08:42 /dev/fd0

root@lkraemer-desktop:/# ls -la /media/floppy0
total 8
drwxr-xr-x 2 root root 4096 2007-10-10 20:55 .
drwxr-xr-x 4 root root 4096 2007-10-12 08:09 ..

root@lkraemer-desktop:/# groups lkraemer
lkraemer : lkraemer adm dialout fax cdrom floppy tape audio dip video 
plugdev scanner netdev lpadmin powerdev admin

root@lkraemer-desktop:/# fdformat /dev/fd0
Double-sided, 80 tracks, 18 sec/track. Total capacity 1440 kB.
Formatting ... done
Verifying ... Read: : Input/output error
Problem reading cylinder 0, expected 18432, read -1

root@lkraemer-desktop:/# fdformat /dev/fd0
Double-sided, 80 tracks, 18 sec/track. Total capacity 1440 kB.
Formatting ... done
Verifying ... Read: : Input/output error
Problem reading cylinder 0, expected 18432, read -1
root@lkraemer-desktop:/# 

When I double click on COMPUTER
a Floppy Drive Icon is displayed along with the CDRW and FILESYSTEM ICONS.

When I right click on the Floppy Drive Icon, and check PROPERTIES
the Owner is UNKNOWN and all ACCESS is READ ONLY for USER, GROUP, OTHER.

Floppy is a NEC FD1231H  P/N 134-506791-302-4 with a Twisted cable to the Motherboard. (Mach Speed K8M8MSR2 Version 1.2 with A11 Bios Update)

Please help me get it working.  I assembled another computer and made it
Dual Boot with Win2K and Ubuntu 7.04 and everything works.  I used the exact same CDR of Ubuntu 7.04 on both machines.  Motherboards were both Mach Speed but the last one was a newer board.

What data do you need to get us able to MOUNT and ACCESS the Floppy.
I have noticed several posts of the same problem with no answers or fixes.

Thanks.

Larry K

---

### Post by arpad on 2007-12-21
Apparently, this isn't much of a problem but I haven't been able to solve it after a couple of hours of futzing around. Everything in the way of problem-description looks pretty much the same other then I'm running Gutsy so I'm not going to throw anything new at this.

Anybody got any ideas?

---

