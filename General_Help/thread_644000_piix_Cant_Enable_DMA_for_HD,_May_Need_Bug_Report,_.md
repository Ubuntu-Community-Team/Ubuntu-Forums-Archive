---
title: "piix: Cant Enable DMA for HD, May Need Bug Report, Help Me Decide"
date: 2007-12-18
forum: General Help
---

### Post by OverclockedMind on 2007-12-18
OK, firstly I apologise if I havent found the post that gives a fix for this, if one is available. I did do quite a bit of searching, not just here but Google as well.

I have a machine that I really would like to get away from Windows on, that uses the piix driver for IDE/ATA. I have noticed that some are having trouble with piix trying to handle things it shouldnt, that isnt my issue.

Mainly, the goal is for me to enable DMA for my hard drive to quicken things on this old box; Win 2000 does UDMA 6 on it with no issues. Ubuntu is using SCSI emulation to deal with things so my hard drive is /dev/sda.

```
joshua@methos:~$ sudo hdparm /dev/sda

/dev/sda:
 IO_support    =  0 (default 16-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 2534/255/63, sectors = 40718160, start = 0
joshua@methos:~$ 

```

```
joshua@methos:~$ sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

```

I can post any relevent lsmod, etc if need be.

I see several threads that are somewhat related to this problem with no solution. From the research I have done, I have heard this may be a problem that could be solved by me compiling a kernel myself, and that it isnt just an issue with Ubuntu but that it spans the various distributions. If compiling will do it, I am up for going for it. I have compiled programs from source before, I could probably get through it.

Am I doing it wrong? If not, I would assume that posting in the forums isnt the way to get it fixed, the answer is file a bug report and I can do that if it truly needs one (it will be my first bug report.)

Just hoping that someone with more knowledge on this will step in to have a look, maybe have me post more info, and then tell me if i can fix it for now with my own compiled kernel, and if I should file a bug report.

Thanks, and warmest regards,
Joshua

---

### Post by OverclockedMind on 2007-12-19
In case this answers the question for someone else in the future:

```
joshua@methos:~$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=Maxtor 6E020L0                          , FwRev=NAR61590, SerialNo=E15EF8ME            
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=40718160
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

joshua@methos:~$ 

```

So the drive is running UDMA, according to the output of this command.

I assume that -i is the one to go by?

If in fact it is, then the lesson is: UDMA is enabled; use hdparm -i (as in Igloo.)

It would have been nice to see a response in the 24 hours that I waited. I am sure there is some reason why this didnt happen though.

Best regards,
Joshua

---

### Post by Whiffle on 2007-12-19
So is DMA working or not?

And yeah, i'm quite familiar with this problem.  It does span the different distributions since is a kernel issue.  On this laptop I ended up recompiling my kernel to get it to work the way I wanted. I  took out almost all of the IDE drivers, except for those related to PCMCIA, so I could still use my pcmcia compactflash adapter.   Mine uses the ata_piix driver and libata.  I have to pass 
```

libata.atapi_enabled=1

```

to my kernel on bootup so that it will run ide atapi devices such as my dvd drive

thinkwiki has some info on this as well:
[http://www.thinkwiki.org/wiki/How_to_configure_and_use_libata_SATA_/_PATA_drivers](http://www.thinkwiki.org/wiki/How_to_configure_and_use_libata_SATA_/_PATA_drivers)

[http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux](http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux)

---

### Post by OverclockedMind on 2007-12-19
As to whether DMA is enabled or not, honestly I do not know. I was going to benchmark the machine and use those results to determine which command gave the correct response, and which one did not... but I haven't gotten there yet, as I am not in front of the machine right now.

I was hoping that someone who knows might happen by and answer authoritatively. But I will try and do the benchmarking, then post again with results, and lesson learned. 

I post back whatever I find out when an answer wasn't given; either to give the answer, or an additional clue someone in the same situation might use to find the answer. Hopefully, it helps someone else along the way.

Best regards,
Joshua

---

### Post by Whiffle on 2007-12-19
hdparm -d /dev/sda

will tell you if dma is on.

---

### Post by OverclockedMind on 2007-12-19
```
joshua@methos:~$ sudo hdparm -d /dev/sda

/dev/sda:

```

---

### Post by OverclockedMind on 2007-12-20
```
joshua@methos:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   238 MB in  2.01 seconds = 118.59 MB/sec
 Timing buffered disk reads:   86 MB in  3.02 seconds =  28.48 MB/sec

```

---

### Post by Whiffle on 2007-12-20
For Reference:

```

root@blacktop:/home/andy# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1476 MB in  2.00 seconds = 737.98 MB/sec
 Timing buffered disk reads:  118 MB in  3.04 seconds =  38.80 MB/sec
root@blacktop:/home/andy# hdparm -i /dev/sda

/dev/sda:

 Model=ST9120821A                              , FwRev=3.04    , SerialNo=            5PL09EL9
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=234441648
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 2:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode

```

Thinkpad T43, using ata_piix driver, Seagate Momentus 5400 rpm 120GB hard drive, intel ICH6 chipset.
kernel 2.6.22.12

---

