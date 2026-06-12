---
title: "how to correctly check write speed of HHD"
date: 2014-07-21
forum: General Help
---

### Post by joan_carles2 on 2014-07-21
In some blog I've seen that we can check write speed of our hard drive with next command:

[FONT=Arial]dd if=/dev/zero of=/tmp/test.dat bs=512 count=2000000

Can anyone explain what is doing this command?

From my understanding I think that this command gives you the equivalent write speed of copying 2000000 archives of 512 bytes. Is that correct? Then if I modify the command to next 

[/FONT][FONT=Arial]dd if=/dev/zero of=/tmp/test.dat bs=1024 count=1000000

This would be the write speed to copy 1000000 archives of 1024 bytes

Is that correct or My understanding is wrong
[/FONT]

---

### Post by tgalati4 on 2014-07-21
The count simply gives the total number of blocks written.  The block size (bs) can vary depending on if you want to simulate small files or large files.  In this example, you are writing 1 megabyte of zeros to a file called test.dat located in the temporary directory (/tmp).  You can use 512, 1024, 2048, 4096, etc for block size.  Your write performance will be pretty close to the same for small block sizes (1 to 64K).  Run a few examples and compare the times.  Most large, modern disks expect a block size of 4096 bytes.  Older disks used 512 or 1024 bytes.

There are many ways you can use the *dd* command:

```
man dd
```

Spacebar to page forward, "q" to quit.

> tgalati4@Mint14-Extensa ~ $ sudo smartctl -a /dev/sda
[sudo] password for tgalati4: 
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.5.0-48-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio Blue Serial ATA
Device Model:     WDC WD1600BEVS-22RST0
Serial Number:    WD-WXC907006646
LU WWN Device Id: 5 0014ee 2ab33009a
Firmware Version: 04.01G04
User Capacity:    160,041,885,696 bytes [160 GB]
**Sector Size:      512 bytes logical/physical**
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Jul 21 15:03:10 2014 PDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


---

### Post by joan_carles2 on 2014-07-22
I understand what you mean. My hard disk is an old one. Block size is 512 bytes

Now I just hesitate if to correctly check the speed bs must be equal to the block size of the hard disk. Or maybe bs it's just to check the speed considering next situations:
1- Bs 512 and count very 2000.0000 gill gives us the write speed of copying such a lot of small archives in our PC
2- BS 500M  and count 2 will give the write speed of copying 2 big archives in our PC.

I understand what I've jsut explained. Blcok size of our hard drive shouldn't be imporant to check the speed correct? doesnt matter of the block size is 512, 4096 or whaever.

---

### Post by sandyd on 2014-07-22
> **joan_carles2 said:**
> In some blog I've seen that we can check write speed of our hard drive with next command:

[FONT=Arial]dd if=/dev/zero of=/tmp/test.dat bs=512 count=2000000

Can anyone explain what is doing this command?

From my understanding I think that this command gives you the equivalent write speed of copying 2000000 archives of 512 bytes. Is that correct? Then if I modify the command to next 

[/FONT][FONT=Arial]dd if=/dev/zero of=/tmp/test.dat bs=1024 count=1000000

This would be the write speed to copy 1000000 archives of 1024 bytes

Is that correct or My understanding is wrong
[/FONT]

Use conv=fdatasync unless your looking to test the speed of your RAM buffer (write cache)

For example, 
```

dd if=/dev/zero of=/tmp/test.dat bs=1024 count=1000000 conv=fdatasync
```

Quick explanation of the different dd options is avaliable at [https://romanrm.net/dd-benchmark](https://romanrm.net/dd-benchmark)

---

