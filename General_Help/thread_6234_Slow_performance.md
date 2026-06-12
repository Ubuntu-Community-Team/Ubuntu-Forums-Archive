---
title: "Slow performance"
date: 2004-11-26
forum: General Help
---

### Post by gborbolla on 2004-11-26
Hi everyone,

I own a Dell Inspiron 8200 and installed Ubuntu on it a couple of weeks ago, and everything was working fine.

I reported to dell support that I have been having troubles reading from de CDROM so yesterday, they sent over a guy to replace the unit, after he replaced the unit the performance of Ubuntu have been bad, I takes about 8 minutes to boot up the machine and login to my account before it will take only a couple of minutes.

I don't know where to start looking up for the error, I have search for something weird in the logs but everything seems ok.

The specs of the machine are:

P4 Mobile @ 1.9Ghz
512Mb RAM
HD 30Gb
CD-RW/DVD Combo
Nvidia GeForce2 32Mb

Hope anyone has any idea where to look for answers or even better how to fix the problem.

Thanks in advance.

German Borbolla

---

### Post by p!=f on 2004-11-26
Do you experience the slowdown after the drive replacement?

---

### Post by gborbolla on 2004-11-26
Yes, everything was working great before the replacement

---

### Post by p!=f on 2004-11-26
[QUOTE=gborbolla]Yes, everything was working great before the replacement[/QUOTE]
Perhaps that guy connect the CD drive on the same IDE channel as the harddrive which is not recommended and indeed may slow things down. It also may be other problem but I'm pretty sure it has something to do with that drive set up.
Could you try the command as follows and post the output here?
```

 * 17:06:34 * pef @ agonicus *
[~] > ls -l /dev/cdrom
lrwxrwxrwx  1 root root 3 2004-11-26 13:30 /dev/cdrom -> hdc

```
Anyway, I suppose you don't have a permission to open the computer case so calling the DELL hotline and explaining the situation might be more effective.

---

### Post by gborbolla on 2004-11-26
Here it is, by the way harddrive is /dev/hda, it has 7 partitions (2 for windows, the rest for linux):

```
panda@gborbos:~ $ ls -l /dev/cdrom
lrwxrwxrwx    1 root     root            3 2004-11-26 08:52 /dev/cdrom -> hdb

```

> Perhaps that guy connect the CD drive on the same IDE channel as the harddrive which is not recommended and indeed may slow things down. It also may be other problem but I'm pretty sure it has something to do with that drive set up.

I was thinking the same, but i don't know how to check it, I was watching while he connected everything and it seems ok, maybe he missed something.

Thanks for the help

---

### Post by p!=f on 2004-11-26
[QUOTE=gborbolla]
```
panda@gborbos:~ $ ls -l /dev/cdrom
lrwxrwxrwx    1 root     root            3 2004-11-26 08:52 /dev/cdrom -> hdb

```
[/QUOTE]
Hdb is not optimal. It means it's the primary slave on IDE channel 0 (primary IDE) with the hard drive as the primary master.
If you can, turn the computer off, unplug data cable from the CD drive and then boot to check the difference.

If you get positive results and have at least basic knowledge of computer components you might want to fix the issue yourself. You will need second IDE data cable and reconnect the CD drive on IDE channel 1 (secondary IDE). It should not matter whether as a secondary slave or as a secondary master.

---

### Post by gborbolla on 2004-11-26
[QUOTE=p!=f]Hdb is not optimal. It means it's the primary slave on IDE channel 0 (primary IDE) with the hard drive as the primary master.
If you can, turn the computer off, unplug data cable from the CD drive and then boot to check the difference.

If you get positive results and have at least basic knowledge of computer components you might want to fix the issue yourself. You will need second IDE data cable and reconnect the CD drive on IDE channel 1 (secondary IDE). It should not matter whether as a secondary slave or as a secondary master.[/QUOTE]

The only problem is that the computer is a laptop, I really don't know of laptops components, if it were a desktop I would not have any problem playing with the components.   :sad: 

I'll try to remove the cd unit from the machine and see what happens.

---

### Post by gborbolla on 2004-11-26
I've removed the unit and reboot the machine and performance is a little better but not as before, so it maybe the unit as slave.

Any ideas?

I'll try to put unit a secondary master.

---

### Post by p!=f on 2004-11-26
How about ask that guy what did he do exactly? Or perhaps better to ask DELL for clarification why is your computer so slow after the replacement?
We may search for a needle in a field here.

---

### Post by astoltz on 2004-11-26
[QUOTE=p!=f]Hdb is not optimal. It means it's the primary slave on IDE channel 0 (primary IDE) with the hard drive as the primary master.[/QUOTE]

Just curious why you say that having a cdrom on hdb is not optimal. I've never heard that before.

---

### Post by p!=f on 2004-11-26
[QUOTE=astoltz]Just curious why you say that having a cdrom on hdb is not optimal. I've never heard that before.[/QUOTE]
Some words to read...

> 
By its very nature, each IDE/ATA channel can only deal with one request, to one device, at a time. **You cannot even begin a second request, even to a different drive, until the first request is completed.** This means that if you put two devices on the same channel, they must share it. In practical terms, this means that any time one device is in use, the other must remain silent. In contrast, two disks on two different IDE/ATA channels can process requests simultaneously on most motherboards. The bottom line is that the best way to configure multiple devices is to make each of them a single drive on its own channel, if this is possible. (This restriction is one major disadvantage of IDE compared to SCSI).

Hard disk controllers on modern systems support running the master and slave device at different speeds, if one supports faster transfer modes than the other. Some systems, however, especially older ones, do not. **If you are using two devices with radically different maximum transfer rates, and the chipset doesn't support independent timing, you will slow down the faster device to the speed of the slower one.**

There are several reasons why optical drives (or other ATAPI devices) should not be shared on the same channel as a fast hard disk. ATAPI allows the use of the same physical channels as IDE/ATA, but it is not the same protocol; **ATAPI uses a much more complicated command structure**. Opticals are also generally much slower devices than hard disks, so they can slow a hard disk down when sharing a channel. Finally, **some ATAPI devices cannot deal with DMA bus mastering drivers, and will cause a problem if you try to enable bus mastering for a hard disk on a channel they are using.**


---

### Post by grille357 on 2004-11-27
Hallo!
In my opinion the idea of CDROM and IDE-Harddisks shouldn't use the same bus is obsolete. There are no new CDROM-Drives without DMA-support and on the contrary it was said before burnproof that you shouldn't use CDROM and Burner on the same channel.
Besides on a laptop you can't change the channel. 
I would check if the DMA and 32bit-options (hdparm) are on. 

Greetings,

Carsten

---

### Post by astoltz on 2004-11-27
[QUOTE=grille357]Hallo!
In my opinion the idea of CDROM and IDE-Harddisks shouldn't use the same bus is obsolete. There are no new CDROM-Drives without DMA-support and on the contrary it was said before burnproof that you shouldn't use CDROM and Burner on the same channel.
Besides on a laptop you can't change the channel. 
I would check if the DMA and 32bit-options (hdparm) are on. 

Greetings,

Carsten[/QUOTE]
 Thanks for the info.  I guess I'll move my cdrom over to the secondary IDE channel.  It can't hurt, even if it doesn't help much.

  -Al

---

### Post by astoltz on 2004-11-27
I decided to try a VERY un-scientific test while switching my cdrom from primary slave to secondary master (I only have two IDE devices curently).  I ran
```
hrparm -t /dev/hda
``` both while the sytem was idle and while the system was reading a large file off the cdrom.  I ran the benchmark before and after switching the cdrom from IDE1 to IDE2.

Results are as follows:

**With CDROM on PRIMARY SLAVE (hdb)**
****System otherwise Idle****
root@StoltzHome:~ # hdparm -t /dev/hda  
/dev/hda:

 Timing buffered disk reads:  138 MB in  3.01 seconds =  45.80 MB/sec

****System reading from CDROM****
root@StoltzHome:~ # hdparm -t /dev/hda
/dev/hda:

 Timing buffered disk reads:  113 MB in  3.02 seconds =  37.51 MB/sec

----------------------------------------------------------------------------------------
**With CDROM on SECONDARY MASTER (hdc)**
****System otherwise Idle****
root@StoltzHome:~ # hdparm -t /dev/hda  
/dev/hda:

 Timing buffered disk reads:  138 MB in  3.02 seconds =  45.66 MB/sec

****System reading from CDROM****
root@StoltzHome:~ # hdparm -t /dev/hda
/dev/hda:

 Timing buffered disk reads:  138 MB in  3.01 seconds =  45.78 MB/sec


Like I say, VERY un-scientific - but interesting that I get esentially unchanged harddisk  throughput with the cdrom on IDE2 as opposed to **18% slower** with the cdrom on IDE1.  I repeated the hdparm benchmark a few times and these results were typical.

I think I'll keep it on IDE2.

   -Al

---

### Post by p!=f on 2004-11-27
```

sudo hdparm -tT /dev/hda

```
-T   perform cache read timings

---

### Post by gborbolla on 2004-12-01
Hello again, sorry I haven't answered but I have been a little busy at work

The problem just got a little more weird... I installed some software from a CD and left the disc inside the unit, and I noticed the system was running better so I did some tests with "hdparm -Tt /dev/hda" and here are the results

With CD inside: around 17.99 MB/sec
Without CD inside: another surprise, the performance is unstable it can go from 1MB/sec to 7MB/sec

I tried playing with hdparm but haven't got any results.

If anyone has an idea I would thank it.

By the way, In windows the performance is ok.

---

### Post by p!=f on 2004-12-01
```

sudo hdparm -i /dev/hda
sudo hdparm -i /dev/hdb

```
and post it here please...

---

### Post by gborbolla on 2004-12-01
[QUOTE=p!=f]```

sudo hdparm -i /dev/hda
sudo hdparm -i /dev/hdb

```
and post it here please...[/QUOTE]
*******************************************
With disc inside

panda@gborbos:~ $ sudo hdparm -i /dev/hda

/dev/hda:

 Model=TOSHIBA MK3018GAS, FwRev=Q3.03 D, SerialNo=624H4975T
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=46
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=58605120
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: device does not report version:

 * signifies the current active mode

panda@gborbos:~ $ sudo hdparm -i /dev/hdb

/dev/hdb:

 Model=HL-DT-STCD-RW/DVD-ROM GCC-4240N, FwRev=D110, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no
 Drive conforms to: device does not report version:

 * signifies the current active mode

*****************************************
Without disc inside
panda@gborbos:~ $ sudo hdparm -i /dev/hda

/dev/hda:

 Model=TOSHIBA MK3018GAS, FwRev=Q3.03 D, SerialNo=624H4975T
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=46
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=58605120
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: device does not report version:

 * signifies the current active mode

panda@gborbos:~ $ sudo hdparm -i /dev/hdb

/dev/hdb:

 Model=HL-DT-STCD-RW/DVD-ROM GCC-4240N, FwRev=D110, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no
 Drive conforms to: device does not report version:

 * signifies the current active mode

---

### Post by p!=f on 2004-12-01
Try to run this...
```

sudo hdparm -d 1 -A 1 -m 16 -u 1 -c 1 /dev/hda

```
... and then benchmark with...
```

sudo hdparm -tT /dev/hda

```

Please post any command outputs within [ code ] [ /code] (without spaces) next time. It's more readable. :)

---

### Post by gborbolla on 2004-12-01
Sorry about the missing tags, here is the output for the commands.

With disc inside
```

panda@gborbos:~ $ sudo hdparm -Tt /dev/hda

/dev/hda:
 Timing buffer-cache reads:   1300 MB in  2.00 seconds = 650.10 MB/sec
 Timing buffered disk reads:   60 MB in  3.02 seconds =  19.90 MB/sec
panda@gborbos:~ $ sudo hdparm -Tt /dev/hda

/dev/hda:
 Timing buffer-cache reads:   1300 MB in  2.00 seconds = 649.13 MB/sec
 Timing buffered disk reads:   46 MB in  3.07 seconds =  14.99 MB/sec
panda@gborbos:~ $ sudo hdparm -Tt /dev/hda

/dev/hda:
 Timing buffer-cache reads:   1276 MB in  2.00 seconds = 636.51 MB/sec
 Timing buffered disk reads:   54 MB in  3.07 seconds =  17.58 MB/sec


```

Without disc inside
```

panda@gborbos:~ $ sudo hdparm -Tt /dev/hda

/dev/hda:
 Timing buffer-cache reads:   1292 MB in  2.00 seconds = 645.45 MB/sec
 Timing buffered disk reads:   28 MB in  4.50 seconds =   6.22 MB/sec
panda@gborbos:~ $ sudo hdparm -Tt /dev/hda

/dev/hda:
 Timing buffer-cache reads:   1256 MB in  2.00 seconds = 627.47 MB/sec
 Timing buffered disk reads:   16 MB in  5.28 seconds =   3.03 MB/sec
panda@gborbos:~ $ sudo hdparm -Tt /dev/hda

/dev/hda:
 Timing buffer-cache reads:   1252 MB in  2.00 seconds = 624.53 MB/sec
 Timing buffered disk reads:   12 MB in  5.33 seconds =   2.25 MB/sec


```

Thanks for your help

---

### Post by gborbolla on 2004-12-01
Sorry missed one output

```

panda@gborbos:~ $ sudo hdparm -d 1 -A 1 -m 16 -u 1 -c 1 /dev/hda
Password:

/dev/hda:
 setting 32-bit IO_support flag to 1
 setting multcount to 16
 setting unmaskirq to 1 (on)
 setting using_dma to 1 (on)
 setting drive read-lookahead to 1 (on)
 multcount    = 16 (on)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)

```

---

### Post by wallijonn on 2004-12-01
Can you go into the BIOS and look at the settings for the disk & cdrom?

---

### Post by gborbolla on 2004-12-01
[QUOTE=wallijonn]Can you go into the BIOS and look at the settings for the disk & cdrom?[/QUOTE]

Ok, done it, nothing really that could give some answers computer is a laptop so BIOS don't even display if disk and cdrom are masters or slaves... 

Thanks for your answer

---

### Post by jdong on 2004-12-01
Hmm, from the hdparm -i results, it would seem like /dev/hda has NO DMA enabled. Try adding **hdparm -X69 /dev/hda**.

**CAUTION:** Enables UDMA-5 for current Linux session. Save all files before continuing -- just in case.

---

### Post by gborbolla on 2004-12-01
[QUOTE=jdong]Hmm, from the hdparm -i results, it would seem like /dev/hda has NO DMA enabled. Try adding **hdparm -X69 /dev/hda**.

**CAUTION:** Enables UDMA-5 for current Linux session. Save all files before continuing -- just in case.[/QUOTE]

Thanks for the help.

Done the read throughput when there is a disc in unit have been improved, but when there is no disc the performance is about the same

I'm guessing that when system is trying to read from harddrive it also tries to read from cd, and because there is no disc loaded it hangs up while trying, it seems a little unlikely, but i don't know what else can be causing the problem.

---

