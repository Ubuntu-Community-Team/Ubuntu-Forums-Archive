---
title: "Loud Hard Drive Noises"
date: 2007-05-04
forum: General Help
---

### Post by Baldwin on 2007-05-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109781](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109781) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've submitted a bug to launchpad [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109781](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109781), but no one has paid any attention to it so I thought I would post here.

After upgrading to feisty from edgy, my hard drive is being very noisy.

Whenever I do something that requires the HDD to work (eg. startup or opening something like OOo), it makes this horrible sound. Under edgy it was essentially silent, same deal under windows.

Anyone got any idea what I can do ?

I've tried "noatime" and disabling swap, no improvement.

If anyone else has the same problem, please go to launchpad and voice your support for my bug report.

Thanks...

---

### Post by dcstar on 2007-05-04
> **Baldwin said:**
> 
Whenever I do something that requires the HDD to work (eg. startup or opening something like OOo), it makes this horrible sound. Under edgy it was essentially silent, same deal under windows.
..........

All that could mean is that now you are using a part of the hard disk where there are bad blocks, and any "noise" is because the hard disk is furiously attempting to re-read those sectors to get your data.

---

### Post by Baldwin on 2007-05-04
I don't think it is bad blocks, but I'm willing to conisder the possibility.

Any advice on how I could check to see if that is the case ?

---

### Post by Maksim on 2007-05-04
I'm having the same problem, is anybody got a solution for it? 

My hardware is almost the same that Baldwin has. Upgraded from Edgy to Fiesty on AMD64, SATA Seageate HDD. 

Thanks!

---

### Post by m.musashi on 2007-05-04
Download the ultimate boot CD and use one of the tools to check the drive.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by Baldwin on 2007-05-04
I didn't have much luck downloading the ultimate boot cd, but I've done a couple of other hard drive checks which have found no errors.

Please note that I can select the old edgy kernel and booting is almost silent, but when I select the feisty kernel it is extremely loud...

---

### Post by m.musashi on 2007-05-04
Are we talking about the same drive and the same partiton? If you can boot either edgy or feisty then they are at least in different partitions (unless you did an upgrade and both kernels exist on the same install). It's possible that the feisty partition has problems but the edgy one doesn't. Loud drive noises are not normal and usually indicate an impending failure or other problem.

---

### Post by tgalati4 on 2007-05-05
Here are some other possibilities:

Is the Feisty partition much smaller than the Edgy partition?  Is the swap drive properly set up under Feisty?  The disk thrashing could be normal if Feisty is using swap while Edgy is running in ram with few swaps.

You can install smartmontools and examine SMART messages and also perform non-destructive tests.  You will get power-on estimates in hours as well as start-stop cycles and temperature extremes.

There is also a quiet setting (man hdparm) that may be set in Edgy and not set in Feisty.  To get more performance, you normally want a little noise--this basically pumps up the swing current so the heads can track faster.  The quiet setting reduces the swing current so it takes a little longer to find tracks.






Or your disk is ready to take a dump.

---

### Post by Baldwin on 2007-05-05
> **m.musashi said:**
> Are we talking about the same drive and the same partiton? If you can boot either edgy or feisty then they are at least in different partitions (unless you did an upgrade and both kernels exist on the same install). 

Yes, the same partition. I did an upgrade which left the old kernel behind (as "previous" in the boot menu).
Of course, thanks to graphics drivers, I can't use a GUI with the old kernel any more.

> **tgalati4 said:**
> Here are some other possibilities:

Is the Feisty partition much smaller than the Edgy partition?  Is the swap drive properly set up under Feisty?  The disk thrashing could be normal if Feisty is using swap while Edgy is running in ram with few swaps.

You can install smartmontools and examine SMART messages and also perform non-destructive tests.  You will get power-on estimates in hours as well as start-stop cycles and temperature extremes.

There is also a quiet setting (man hdparm) that may be set in Edgy and not set in Feisty.  To get more performance, you normally want a little noise--this basically pumps up the swing current so the heads can track faster.  The quiet setting reduces the swing current so it takes a little longer to find tracks.

Since I did an upgrade, I'm assuming the swap settings are ok. I have tried disabling swap but it didn't make the noises go away.

I'll investigate smartmontools and hdparm, thanks for the tips. Do you know if windows would use the quiet mode ? (in windows the drive is almost silent)

---

### Post by Baldwin on 2007-05-05
I have tried to set the "acoustic management" in hdparm, but no luck:
```

$ sudo hdparm -M /dev/sda

/dev/sda:
 HDIO_GET_ACOUSTIC failed: Inappropriate ioctl for device

```

however, "hdparm -I" indicates that it is set to 0 (off) under both the old (quiet) kernel and the new (horrible noise making) kernel.
```
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Recommended acoustic management value: 128, current value: 0
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
                SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    DOWNLOAD_MICROCODE
                SET_MAX security extension
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
           *    SATA-I signaling speed (1.5Gb/s)
           *    Native Command Queueing (NCQ)
           *    Phy event counters
           *    Software settings preservation

```

smartctl (smartmontools) tells me "Device does not support SMART", which I guess is because SMART is disabled somehow (based on above hdparm output). I'll try and fix that.

Any more ideas ? I'm pretty confident it's not a "drive is dying" thing because a different kernel on the same partition is quiet; and accessing my FAT partitions is noisy from linux, but not from windows...


Thanks for the advice so far, at least I've learned about some hard drive tools :)

---

### Post by tgalati4 on 2007-05-05
sudo smartctl -s on /dev/sda

Should turn SMART on for the drive.  

sudo hdparm -iI /dev/sda (that's small i and capital I)

should confirm that SMART is turned on.

sudo smartctl -t short /dev/sda

will run a short test (a few minutes--non-destructive and you can have the drive mounted and continue to surf the web.)

sudo smartctl -t long /dev/sda

will run a long test (an hour or so, better to let it finish without much user interference)

To view the results after each test:

sudo smartctl -l selftest /dev/sda (-list)

Will list the results of either the short or long test.

sudo smartctl -a /dev/sda 

will print out a complete listing of current SMART metrics.

It's a decent tool that will give you a little more insight.

It may not solve your problem, but if you can isolate the difference in drive performance between distros then it may point in the right direction.

Post the output of:

sudo hdparm -tT /dev/sda

In both distributions.

Good luck.

---

### Post by Baldwin on 2007-05-07
> **tgalati4 said:**
> sudo smartctl -s on /dev/sda

Should turn SMART on for the drive.  



Doesn't seem to work. Could it be a motherboard thing stopping SMART? I've looked around in the BIOS to no avail though...
```
smartctl version 5.36 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

unable to fetch IEC (SMART) mode page [unsupported field in scsi command]
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
```

I didn't try any of the other smartctl things as I suspect they won't work anyway with SMART off...

> **tgalati4 said:**
> 
sudo hdparm -tT /dev/sda

In both distributions.

I ran it twice on each, with a "uname -a" at the top to show the kernel versions.

Edgy Kernel
```
Linux host_name 2.6.17-11-generic #2 SMP Tue Mar 13 22:06:20 UTC 2007 x86_64 GNU/Linux

/dev/sda:
 Timing cached reads:   1632 MB in  2.00 seconds = 815.43 MB/sec
 Timing buffered disk reads:  202 MB in  3.02 seconds =  66.82 MB/sec

/dev/sda:
 Timing cached reads:   1570 MB in  2.00 seconds = 784.49 MB/sec
 Timing buffered disk reads:  198 MB in  3.00 seconds =  65.91 MB/sec

```

Feisty Kernel
```
Linux host_name 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux

/dev/sda:
 Timing cached reads:   1556 MB in  2.00 seconds = 777.73 MB/sec
 Timing buffered disk reads:  202 MB in  3.01 seconds =  67.18 MB/sec

/dev/sda:
 Timing cached reads:   1570 MB in  2.00 seconds = 785.02 MB/sec
 Timing buffered disk reads:  202 MB in  3.02 seconds =  66.85 MB/sec

```

Edgy kernel didn't have a GUI running, feisty did. No network connections up, nothing running other than whatever loads on boot. There's not much difference between them...

---

