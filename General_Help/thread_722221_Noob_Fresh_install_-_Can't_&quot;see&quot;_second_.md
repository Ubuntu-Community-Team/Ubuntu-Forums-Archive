---
title: "Noob: Fresh install - Can't &quot;see&quot; second hard drive"
date: 2008-03-12
forum: General Help
---

### Post by PremiumPete83 on 2008-03-12
I just installed Ubuntu 7.1 on a second partition of my main drive and everything is going well except that my Western Digital hard drive isn't being detected.  When I do an fdisk it doesn't display any second drive.  Also, when I look into devices I do see my High Point 302 PCI IDE adapter and an IDE device under it (I use the High Point 133 IDE card for my legacy hard drive) but the IDE device isn't recognized as a Western Digital 80 gig with 2 partitions.  

Is there any way to get this device available?  It is using NTFS, but I just really wanted to read the MP3 directory as I have a large collection and like to listen to music..

---

### Post by Zorael on 2008-03-12
So there's a whole device missing? Not just a partition?

What does the following command output, entered in a console?
```
$ ls /dev/sd*
```

---

### Post by Fire_Chief on 2008-03-12
The drive may appear at a higher /dev/hd*x* reference like /dev/hde or /dev/hdf. If you look at your dmesg log, do you see any messages about the card and/or messages about the drives detected on bootup?

```
cat /var/log/dmesg | grep ata
```
and
```
cat /var/log/dmesg | grep sd
```
or
```
cat /var/log/dmesg | grep hd
```


That should tell you all of the SCSCI, IDE, and SATA devices detected by the system regardless of whether they are mounted or not. Since you said the card shows up with an IDE device under it, this will tell you what the mount path would be for the two partitions (i.e. /dev/hde1 & /dev/hde2).

Cheers!

---

### Post by PremiumPete83 on 2008-03-12
I'll do those commands when I get home from work and let you know.

Yes, the whole device is missing when doing an FDISK.  I have two 80 gig HDs in my current rig but only the one SATA shows up (which has two partitions - Vista/Ubuntu).  Those devices (partitions) show up as /dev/hda3 and dev/hda4.  

I'm assuming if they are on a separate drive from my understanding then both partitions should be /dev/hde1 and /dev/dhe2, correct? (This is my 2nd day playing with Linux)

---

### Post by PremiumPete83 on 2008-03-12
Here are the first two commands:

> 
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sda4  /dev/sda5
pete@pete-desktop:~$ cat /var/log/dmesg | grep ata
[    0.000000]  BIOS-e820: 000000003fee3000 - 000000003fef0000 (ACPI data)
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[   28.404779] Memory: 1020836k/1047424k available (2274k kernel code, 26196k reserved, 1185k data, 296k init)
[   32.573968] libata version 2.21 loaded.
[   32.819951] sata_nv 0000:00:0e.0: version 3.4
[   32.820744] scsi0 : sata_nv
[   32.820797] scsi1 : sata_nv
[   32.820866] ata1: SATA max UDMA/133 cmd 0x00000000000109f0 ctl 0x0000000000010bf2 bmdma 0x000000000001e000 irq 21
[   32.820870] ata2: SATA max UDMA/133 cmd 0x0000000000010970 ctl 0x0000000000010b72 bmdma 0x000000000001e008 irq 21
[   33.294083] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   33.306304] ata1.00: ATA-7: WDC WD800JD-75MSA3, 10.01E04, max UDMA/133
[   33.306307] ata1.00: 156250000 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   33.318282] ata1.00: configured for UDMA/133
[   33.793163] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   33.965000] ata2.00: ATAPI: ATAPI   DVD A  DH20A3S, 9V5P, max UDMA/100
[   34.148668] ata2.00: configured for UDMA/100
[   34.150810] scsi2 : sata_nv
[   34.150878] scsi3 : sata_nv
[   34.150949] ata3: SATA max UDMA/133 cmd 0x00000000000109e0 ctl 0x0000000000010be2 bmdma 0x000000000001cc00 irq 20
[   34.150953] ata4: SATA max UDMA/133 cmd 0x0000000000010960 ctl 0x0000000000010b62 bmdma 0x000000000001cc08 irq 20
[   34.463921] ata3: SATA link down (SStatus 0 SControl 300)
[   34.787326] ata4: SATA link down (SStatus 0 SControl 300)
[   35.320955] EXT3-fs: mounted filesystem with ordered data mode.
[   43.178789]  hde:hde: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[   43.261716] hde: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[   43.361713] hde: status error: status=0x58 { DriveReady SeekComplete DataRequest }


> 
pete@pete-desktop:~$ cat /var/log/dmesg | grep sd
[   34.812365] sd 0:0:0:0: [sda] 156250000 512-byte hardware sectors (80000 MB)
[   34.812378] sd 0:0:0:0: [sda] Write Protect is off
[   34.812381] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.812394] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.812451] sd 0:0:0:0: [sda] 156250000 512-byte hardware sectors (80000 MB)
[   34.812459] sd 0:0:0:0: [sda] Write Protect is off
[   34.812461] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.812472] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.812477]  sda: sda1 sda2 sda3 sda4 < sda5 >
[   34.848204] sd 0:0:0:0: [sda] Attached SCSI disk
[   34.852472] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  224.069223] Adding 1068280k swap on /dev/sda5.  Priority:-1 extents:1 across:1068280k
[  224.299666] EXT3 FS on sda3, internal journal


> 
pete@pete-desktop:~$ cat /var/log/dmesg | grep hd
[   34.802716]     ide2: BM-DMA at 0x8c08-0x8c0f, BIOS settings: hde: DMA, hdf: pio
[   35.091888] hde: , ATA DISK drive
[   43.178737] hde: max request size: 128KiB
[   43.178743] hde: 681472 sectors (348 MB) w/44KiB Cache, CHS=88/88/88
[   43.178748] hde: INVALID GEOMETRY: 88 PHYSICAL HEADS?
[   43.178789]  hde:hde: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[   43.204975] hde: drive not ready for command
[   43.261716] hde: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[   43.262168] hde: drive not ready for command
[   43.361713] hde: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[   43.362046] hde: drive not ready for command
[   73.357046] hde: lost interrupt
[  103.301991] hde: lost interrupt
[  113.283640] hde: lost interrupt
[  113.283645] hde: task_in_intr: status=0x01 { Error }
[  113.283649] hde: task_in_intr: error=0x04 { DriveStatusError }
[  123.265290] hde: lost interrupt
[  123.265293] hde: task_in_intr: status=0x01 { Error }
[  123.265297] hde: task_in_intr: error=0x04 { DriveStatusError }
[  153.210238] hde: lost interrupt
[  163.191887] hde: lost interrupt
[  163.191890] hde: task_in_intr: status=0x01 { Error }
[  163.191894] hde: task_in_intr: error=0x04 { DriveStatusError }
[  173.173536] hde: lost interrupt
[  173.173540] hde: task_in_intr: status=0x01 { Error }
[  173.173543] hde: task_in_intr: error=0x04 { DriveStatusError }
[  203.166396] hde: lost interrupt


That 88 heads thing doesn't look good but I have no idea what it means..

Thanks for your input/help!

---

### Post by PremiumPete83 on 2008-03-12
Could this be a BIOS setting on my 133SB IDE PCI controller?

---

### Post by Fire_Chief on 2008-03-12
Yes, that's the likely cause. If you can, change the addressing in the PCI card BIOS from CHS to LBA or another type. Run the** cat /var/log/dmesg | grep hd** again after the change to see if Linux is now recognizing the drive properly.

This line ```
 43.178743] hde: 681472 sectors (348 MB) w/44KiB Cache, CHS=88/88/88
```will help you determine if the system can see the drive properly (correct size will be reported).

On a side note, do you have any other OS installed on this computer? If so, does it see the drive correctly?

---

### Post by PremiumPete83 on 2008-03-12
I have Vista installed as that does recognize the drive.  By changing that setting Vista should still be able to see the drive, correct?

---

### Post by Fire_Chief on 2008-03-12
I think so...if not, you can always change it back.

---

### Post by PremiumPete83 on 2008-03-12
> **Fire_Chief said:**
> I think so...if not, you can always change it back.

True.  Guess we'll find out when I get home tonight. :)

---

### Post by PremiumPete83 on 2008-03-12
I can't change any settings on the High Point Rocket 133SB BIOS..

Would changing the jumper from auto to slave have any effect on the HD recognition?

---

### Post by PremiumPete83 on 2008-03-13
I was thinking of moving the PCI card to another slot but I doubt that is the issue since the card is found, just that the hard drive isn't being recognized..

---

### Post by PremiumPete83 on 2008-03-13
Well that caused more harm.  Now I can't see my Vista partition and my video card went back to limited graphics mode..

---

### Post by Fire_Chief on 2008-03-13
Yikes! :( That's not what we were hoping for....

I agree that changing the jumper will not affect the visibility of the drive.

Do you happen to have any open IDE ports on the motherboard directly? You may want to plug the drive in there and then see if Linux sees it differently. Since that is a different controller the addressing settings can be adjusted (if needed) in the motherboard BIOS. My hope is that Linux will see the drive fine with no adjustments needed.
If you still see the same kinds of errors from the cat | grep results, then there is the strong possibility that the drive is going (or has gone) bad. :frown:

---

### Post by PremiumPete83 on 2008-03-13
Well I doubt the drive is bad, It's working fine in Vista with no signs of failure..I'll have to do a chkdsk on it to make sure I don't see any failures..

Unfortunately my motherboard has no IDE ports available whatsoever, which is the reason I have this PCI EDI controller card installed..

---

### Post by Fire_Chief on 2008-03-13
So at this point, Vista is working properly and Ubuntu is .... ?

---

### Post by PremiumPete83 on 2008-03-13
Well before I made the change the only thing not working in UBUNTU was that the second drive wasn't displaying..

I switched the card from one PCI slot to another to see if this would do anything and it did.  Now I have an issue with my graphics card loading in limited performance mode, my second hard drive still doesn't show, and now my Vista partition isn't showing which is on the same drive the UBUNTU partition is on..

Now I'm really :confused:

---

### Post by Fire_Chief on 2008-03-13
:? I hate to ask this but do you have a lot of data or added stuff in your Ubuntu system? If not, it may be easier/faster to simply reinstall it. :-(

---

### Post by PremiumPete83 on 2008-03-13
Well not really, but, I originally wanted to install UBUNTU on some free space on the other drive that it won't recognize.  When I loaded live cd for the first time it didn't recognize the drive.  So, I split my windows partition in half and figure I'd figure out why it won't recognize my drive.  Once I figured out why it wouldn't recognize it I'd install it on the second drive..

So, I've had this problem since I've started using Ubuntu.

---

