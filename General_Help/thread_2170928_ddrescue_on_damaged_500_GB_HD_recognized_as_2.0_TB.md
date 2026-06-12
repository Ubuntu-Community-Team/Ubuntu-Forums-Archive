---
title: "ddrescue on damaged 500 GB HD recognized as 2.0 TB-Drive reliable ??"
date: 2013-08-28
forum: General Help
---

### Post by michael51 on 2013-08-28
Hi everybody,
ddrescue is a great piece of software, I allready saved a whole database out of a damagaed HD last year.

Now I'm dealing with a 500 GB 2.5" HD (WD500BEVT) which has fallen down not being used at that moment..

The disk is attached to my test-system via sata2usb-bridge-cable.

The disk starts the spindel for about 10 seconds , some 4 or 5 times you hear this well known click noise.
After that the disk seems to be dead. 

But linux recognizes /dev/sdc , reports trouble with the write through cache .
fdisk -l sees "something" , but "it" has an "unknown partition table"
It assumes an disk with 2,19 / 2.00 Terabytes , I don't know why.

Disk /dev/sdc: 2199.0 GB, 2199023255552 bytes
255 Koepfe(heads), 63 Sektoren/Spur, 267349 Zylinder, zusammen 4294967296 Sektoren
Einheiten = Sektoren von 1  512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Festplattenidentifikation: 0x00000000

Dmesg shows the same:

[  220.364054] usb 1-8: new high-speed USB device number 3 using ehci_hcd
[  220.531270] Initializing USB Mass Storage driver...
[  220.533611] scsi6 : usb-storage 1-8:1.0
[  220.533865] usbcore: registered new interface driver usb-storage
[  220.533870] USB Mass Storage support registered.
[  221.534694] scsi 6:0:0:0: Direct-Access             PQ         : 0 ANSI: 2 CCS
[  221.536458] sd 6:0:0:0: Attached scsi generic sg3 type 0
[  221.539790] sd 6:0:0:0: [sdc] Very big device. Trying to use READ CAPACITY(16).
[  221.541999] sd 6:0:0:0: [sdc] Using 0xffffffff as device size
[  221.542018] sd 6:0:0:0: [sdc] 4294967296 512-byte logical blocks: (2.19 TB/2.00 TiB)
[  221.543801] sd 6:0:0:0: [sdc] Write Protect is off
[  221.543814] sd 6:0:0:0: [sdc] Mode Sense: 00 38 00 00
[  221.545579] sd 6:0:0:0: [sdc] Asking for cache data failed
[  221.563600] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  221.584914] sd 6:0:0:0: [sdc] Very big device. Trying to use READ CAPACITY(16).
[  221.586906] sd 6:0:0:0: [sdc] Using 0xffffffff as device size
[  221.589528] sd 6:0:0:0: [sdc] Asking for cache data failed
[  221.606856] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  221.646043]  sdc: unknown partition table
[  221.648908] sd 6:0:0:0: [sdc] Very big device. Trying to use READ CAPACITY(16).
[  221.650924] sd 6:0:0:0: [sdc] Using 0xffffffff as device size
[  221.655562] sd 6:0:0:0: [sdc] Asking for cache data failed
[  221.672279] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  221.688898] sd 6:0:0:0: [sdc] Attached SCSI disk


I startet a "ddrescue -n /dev/sdc /space/myImage.img logfile.txt" (ubuntu 12_04 ddrescue V1.14)
And it works !!!,  very slowly (587 kB/s) ,but it already "rescued" nearly 70 GB in 40 hours,
There seem to be no errors at all.
It reports "errors : 0" , everything on the disk seems to be readable.

It continues rescueing after the restart counting up correctly the block numbers.
I can stop the job , in the log the actual block number is listed,

"
....
# Rescue Logfile. Created by GNU ddrescue version 1.14
# Command line: ddrescue -n /dev/sdc rettung.iso logfile.log
# current_pos  current_status
0x1021960000     ?
#      pos        size  status
0x00000000  0x1021960000  +
0x1021960000  0x1EFDE6A0000  ?"


ddrescue -n /dev/sdc rettung.iso logfile.log

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:    69282 MB,  errsize:       0 B,  errors:       0
Current status
rescued:    69290 MB,  errsize:       0 B,  current rate:     524 kB/s
   ipos:    69290 MB,   errors:       0,    average rate:     561 kB/s
   opos:    69290 MB,     time from last successful read:       0 s
Copying non-tried blocks...



My question: Can this be a bug in ddrescue, or do I simply have to be patient and wait for another 8 days, until the whole disk has been read?
Is ddrescue able to recover data, when there is hardly any spinning of the platters ?

Can I analyze an unfinished image with hexedit, od or something like that, just to see if there's anything else than "..00 00 00 00 00 00..." on it?

As far as I know will I do have to treat the Image afterwards with "testdisk" , testdisk will probably need the correct disk geometry.
ddrescue gets the geometry wrong, which parameters will I have to provide in order to be successfull ?

Thanks , Michael

---

