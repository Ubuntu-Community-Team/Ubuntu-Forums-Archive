---
title: "fsck failure at boot, then fsck failures"
date: 2007-04-26
forum: General Help
---

### Post by Babbleback on 2007-04-26
Apparently my Ubuntu 6.10 desktop-i386 machine is forced to run fsck after 20 boots.  While fsck is executing, and approximately at the same percentage completion, error messages begin to appear.  The same error messages are displayed over and oer as in an infinite loop. The error messages are as follows:

[1771798901.768000] ata1: translated ATA stat/err 0x51/40 to SCI SK/ASC/ASCQ 0x3/11/04

[1771798901.768000] ata1: translated ATA stat/err 0x51/40 to SCI SK/ASC/ASCQ 0x3/11/04

[1771798901.768000] ata1: translated ATA stat/err 0x51/40 to SCI SK/ASC/ASCQ 0x3/11/04

[1771798901.768000] ata1: translated ATA stat/err 0x51/40 to SCI SK/ASC/ASCQ 0x3/11/04

[1771798901.768000] ata1: translated ATA stat/err 0x51/40 to SCI SK/ASC/ASCQ 0x3/11/04

[1771798901.768000] ata1: translated ATA stat/err 0x51/40 to SCI SK/ASC/ASCQ 0x3/11/04

[1771798901.768000]  Buffer I/O error on device sda1, logical block 54722597

---
To further describe the errors displayed above:

The numbers appearing above in []'s change and the number above after logical block increments each iteration of the error display.  The ata1:...0x3//11/04 is always the same.

---

I have tried to CTRL+C, CTRL+Z, and more than I want to admit to no avail during the execution of the forced check of my file system on /dev/sda1.  Execution continues to failure.

---

I loaded the 7.04 desktop-x86_64 live CD on my machine (it is an amd64).  CTRL+ALT+F1 and ran the following at the bash prompt:

sudo tune2fs -i 0 /dev/sda1

Which should have disabled the forced fsck.  I reboot and everything seems ok.  I ran:

sudo fsck /dev/sda1

Which informs me that I should unmount the device. I ran:

umount /dev/sda1

Which returns:

umount: /dev/sda1 mount disagrees with the fstab

I reboot with 7.04 desktop-x86_64 live CD and I ran:

sudo fsck -t ext3 /dev/sda1

Which returns something along the lines of:

[   399.099018]ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   399.099018]ata1.00: (BMDMA stat 0x24)
[   399.099018]ata1.00: cmd 25/00:80:0f:20:18/00:00:1a:00:00/e0 tag 0 cdb 0x0 data 665536 in
[   399.107072] Buffer I/O error on device sda1, logical block 4377780945
[   399.107072] Buffer I/O error on device sda1, logical block 4377780946
[   399.107072] Buffer I/O error on device sda1, logical block 4377780947
[   399.107072] Buffer I/O error on device sda1, logical block 4377780948
[   399.107072] Buffer I/O error on device sda1, logical block 4377780949
[   399.107072] Buffer I/O error on device sda1, logical block 4377780950
[   399.107072] Buffer I/O error on device sda1, logical block 4377780951
[   399.107072] Buffer I/O error on device sda1, logical block 4377780952
[   399.107072] Buffer I/O error on device sda1, logical block 4377780953
[   399.107072] Buffer I/O error on device sda1, logical block 4377780954
[   399.107072] Buffer I/O error on device sda1, logical block 4377780955
[   399.107072] Buffer I/O error on device sda1, logical block 4377780956
Error reading block 547226188 (Attempt to read block from filesystem resulted in short read) while doing inode scan.  Ignore error(y)?

I hit y or enter and get:

Force rewrite(y)

I hit y or enter and get:

Error reading block 547226188 (Attempt to read block from filesystem resulted in short read) while doing inode scan.  Ignore error(y)?

I hit n and write to the forum.

---

### Post by Babbleback on 2007-04-26
So does anyone know how I can fix this file system?  Is there another utility to use to verify if there is a problem with it?  Is this a problem with fsck or my disk?  I thought that fsck was supposed to be able to repair it?

---

### Post by confused57 on 2007-04-26
This link may help:
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)

---

### Post by Babbleback on 2007-04-26
Thanks.  It gave me the same errors as before but at least the -c -c has it checking for bad blocks(non-destructive read-write test) now... looks like its going to take awhile

---

### Post by Babbleback on 2007-04-26
In fact at this rate it is going to take 5 hours.  Guess I'll check it in the morning.  Thanks again!

---

### Post by Babbleback on 2007-04-27
Now i've tried:

e2fsck -c -c -y -v /dev/sda1

and it has been running for many hours..:confused: What options do I have for coping with what appears to be a hard drive with bad sectors?

---

