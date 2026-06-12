---
title: "nautilus gets tired when copying large files?"
date: 2008-06-12
forum: General Help
---

### Post by Arlanthir on 2008-06-12
**EDIT:** It's not nautilus, it's everything that accesses the disk. Still need help.
Problem also occurs when copying from an external HDD to a PSP Device, not using files in the main disk.

Has anyone noticed any loss in speed/performance of nautilus file copy with large files (1GB+)? Note that I don't mean PC performance (as in some threads already posted here), but in the copy itself.

It starts fast, the progress bar filling up nicely and at some point it starts to slow down, taking ages to copy the rest of the file.
It's like each 1% takes longer than the previous one.

Is this because of the recent conversion to gvfs? 
Is this a general bug or am I the only one experiencing it?

Thanks in advance for any clarifications!

---

### Post by iaculallad on 2008-06-12
It's faster when using either gnome-commander or the cp terminal utility. I don't think nautilus "copy-feature" has been fixed yet.

---

### Post by Arlanthir on 2008-06-12
That's a shame :S Thank you ;)

---

### Post by mhousel on 2008-06-12
> **iaculallad said:**
> It's faster when using either gnome-commander or the cp terminal utility. I don't think nautilus "copy-feature" has been fixed yet.I've had the same problem except the system actually freezes (mouse pointer, etc.).
I've also had the same problem using cp from a console window. :confused:

---

### Post by Arlanthir on 2008-06-13
Actually, cp took a large chunk o' while too :S
If it had a progress bar I'd tell you if the same symptoms are true. Argh.

---

### Post by unutbu on 2008-06-13
Arlanthir, I think you need hard data to find out if there is something wrong with your nautilus or cp. 

I did a test to see how long it takes to copy 1MB, 2MB, 4MB, 8MB, 16MB, 32MB, 64MB, 128MB, 512MB, and 1024MB files on my machine. If you want, you can use the script to benchmark your machine. The final result is a graph which shows how long it takes to copy files of various sizes. If the graph is linear and the overall speed is good, then things are probably ok. If something is wrong you would see a marked upward acceleration (concavity) in the graph.

You'll need 4GB free hard drive space to run this script:
```

#!/usr/bin/perl
use strict;
use warnings;

my $drive=shift @ARGV || "/dev/sda";
open(FILE,">","cptimes.dat") || die;
print "Benchmarking $drive\n";
print FILE "Benchmarking $drive\n";
close(FILE);

my $cmd;
$cmd="/usr/bin/time -f '%e' dd if=/dev/zero of=test.1M bs=1 count=1000000";
print "$cmd\n\n";
system($cmd);

my @dat;
for my $num (0..9) {
    my $powerof2=2**$num;
    my $nextpower=2*$powerof2;
    $cmd="/usr/bin/time -f '%e' cat test.${powerof2}M test.${powerof2}M 2>&1 > test.${nextpower}M";
    system($cmd);
}

@dat=();
for my $num (0..10) {
    my $powerof2=2**$num;
    $cmd="/usr/bin/time -f '%e' cp test.${powerof2}M test.${powerof2}M.0 2>&1";
    print "$cmd\n\n";
    open(CAT,"$cmd |") || die;
    while (<CAT>) {	
	my $num=$_;
	chomp($num);
	print "time=$num seconds\n";
	push(@dat,[$powerof2,$num]);
    }
    close(CAT);
}

open(DATA,">>","cptimes.dat") || die;
foreach my $pair (@dat) {
    print DATA "$pair->[0]\t$pair->[1]\n";
}
close(DATA);

for my $num (0..10) {
    my $powerof2=2**$num;
    my $file="test.${powerof2}M";
    unlink($file);
    $file="test.${powerof2}M.0";
    unlink($file);
}

```

Save the script in a file named 'benchmark-hd.pl'. Make it executable:
```
chmod 755 benchmark-hd.pl
```
Put benchmark-hd.pl in a directory which is in your PATH.

To run the script:

```

out@themovies:~/tmp/test% benchmark-hd.pl

14:52:00 out@themovies:~/tmp/test% benchmark-hd.pl
/usr/bin/time -f '%e' dd if=/dev/zero of=test.1M bs=1 count=1000000
1000000+0 records in
1000000+0 records out
1000000 bytes (1.0 MB) copied, 2.72753 seconds, 367 kB/s
2.73


/usr/bin/time -f '%e' cat test.1M test.1M 2>&1 > test.2M
time=0.00 seconds


/usr/bin/time -f '%e' cat test.2M test.2M 2>&1 > test.4M
time=0.01 seconds


/usr/bin/time -f '%e' cat test.4M test.4M 2>&1 > test.8M
time=0.02 seconds


/usr/bin/time -f '%e' cat test.8M test.8M 2>&1 > test.16M
time=0.05 seconds


/usr/bin/time -f '%e' cat test.16M test.16M 2>&1 > test.32M
time=0.10 seconds


/usr/bin/time -f '%e' cat test.32M test.32M 2>&1 > test.64M
time=0.60 seconds


/usr/bin/time -f '%e' cat test.64M test.64M 2>&1 > test.128M
time=3.00 seconds


/usr/bin/time -f '%e' cat test.128M test.128M 2>&1 > test.256M
time=4.66 seconds


/usr/bin/time -f '%e' cat test.256M test.256M 2>&1 > test.512M
time=13.04 seconds


/usr/bin/time -f '%e' cat test.512M test.512M 2>&1 > test.1024M
time=41.90 seconds


/usr/bin/time -f '%e' cp test.1M test.1M.0 2>&1
time=0.29 seconds


/usr/bin/time -f '%e' cp test.2M test.2M.0 2>&1
time=0.04 seconds


/usr/bin/time -f '%e' cp test.4M test.4M.0 2>&1
time=0.10 seconds


/usr/bin/time -f '%e' cp test.8M test.8M.0 2>&1
time=0.16 seconds


/usr/bin/time -f '%e' cp test.16M test.16M.0 2>&1
time=0.59 seconds


/usr/bin/time -f '%e' cp test.32M test.32M.0 2>&1
time=1.36 seconds


/usr/bin/time -f '%e' cp test.64M test.64M.0 2>&1
time=2.45 seconds


/usr/bin/time -f '%e' cp test.128M test.128M.0 2>&1
time=5.23 seconds


/usr/bin/time -f '%e' cp test.256M test.256M.0 2>&1
time=10.11 seconds


/usr/bin/time -f '%e' cp test.512M test.512M.0 2>&1
time=21.67 seconds


/usr/bin/time -f '%e' cp test.1024M test.1024M.0 2>&1
time=32.02 seconds
```

The script will produce a bunch of large files full of zeros. The copy command is timed and the data is put in a file called cptimes.dat.

To plot the data I used gnuplot:

```
out@themovies:~/tmp/test% gnuplot
gnuplot> plot "cptimes.dat" with linespoints
plot "cptimes.dat" with linespoints
gnuplot> quit
quit
out@themovies:~/tmp/test% du -sh .
3.9G	.
out@themovies:~/tmp/test% cat cptimes.dat 
MB	seconds       # This shows how long it takes to copy a file of a certain size.
1	0.17
2	0.08
4	0.11
8	0.15
16	1.01
32	1.26
64	2.32
128	5.48
256	7.37
512	15.08
1024	30.72
```

For large files, the copy speed was roughly linear at 33MB/second. Your copy speed may be different depending on your hard drive type as well as certain configuration parameters that can be set with hdparm. I can point you toward some information on that if you are interested, but I suggest you first benchmark your machine.

---

### Post by Arlanthir on 2008-06-13
I'll run it when I get the chance (just watching the second half of Netherlands-France), but I should point out that generally I copy files to USB devices, such as extern HDD or a PSP. The first one is formatted to ntfs whereas the second I have to check.

I'll post the results later today, I hope. =)

EDIT: First, let me thank you for your benchmark, I was kinda in a hurry before.
Second, I did the benchmark on my machine, only difference was I saved it in my home folder and ran it with ./test.pl

Ehrm. There's definitely something wrong..

```

arlanthir@Icarus:~$ ./test.pl


/usr/bin/time -f '%e' dd if=/dev/zero of=test.1M bs=1 count=1000000
1000000+0 records in
1000000+0 records out
1000000 bytes (1.0 MB) copied, 3.23749 s, 309 kB/s
3.23


/usr/bin/time -f '%e' cat test.1M test.1M 2>&1 > test.2M
time=0.00 seconds


/usr/bin/time -f '%e' cat test.2M test.2M 2>&1 > test.4M
time=0.01 seconds


/usr/bin/time -f '%e' cat test.4M test.4M 2>&1 > test.8M
time=0.03 seconds


/usr/bin/time -f '%e' cat test.8M test.8M 2>&1 > test.16M
time=0.06 seconds


/usr/bin/time -f '%e' cat test.16M test.16M 2>&1 > test.32M
time=0.14 seconds


/usr/bin/time -f '%e' cat test.32M test.32M 2>&1 > test.64M
time=0.22 seconds


/usr/bin/time -f '%e' cat test.64M test.64M 2>&1 > test.128M
time=2.87 seconds


/usr/bin/time -f '%e' cat test.128M test.128M 2>&1 > test.256M
time=23.79 seconds


/usr/bin/time -f '%e' cat test.256M test.256M 2>&1 > test.512M
time=60.97 seconds


/usr/bin/time -f '%e' cat test.512M test.512M 2>&1 > test.1024M
time=101.73 seconds


/usr/bin/time -f '%e' cp test.1M test.1M.0 2>&1
time=1.65 seconds


/usr/bin/time -f '%e' cp test.2M test.2M.0 2>&1
time=0.57 seconds


/usr/bin/time -f '%e' cp test.4M test.4M.0 2>&1
time=0.59 seconds


/usr/bin/time -f '%e' cp test.8M test.8M.0 2>&1
time=1.28 seconds


/usr/bin/time -f '%e' cp test.16M test.16M.0 2>&1
time=2.99 seconds


/usr/bin/time -f '%e' cp test.32M test.32M.0 2>&1
time=4.84 seconds


/usr/bin/time -f '%e' cp test.64M test.64M.0 2>&1
time=7.52 seconds


/usr/bin/time -f '%e' cp test.128M test.128M.0 2>&1
time=16.20 seconds


/usr/bin/time -f '%e' cp test.256M test.256M.0 2>&1
time=36.52 seconds


/usr/bin/time -f '%e' cp test.512M test.512M.0 2>&1
time=52.44 seconds


/usr/bin/time -f '%e' cp test.1024M test.1024M.0 2>&1
time=116.73 seconds


```


```

arlanthir@Icarus:~$ cat cptimes.dat
1	1.65
2	0.57
4	0.59
8	1.28
16	2.99
32	4.84
64	7.52
128	16.20
256	36.52
512	52.44 
1024	116.73

```

I benchmarked without compiz fusion and the results were better but still not normal.

---

### Post by mhousel on 2008-06-13
Not sure if it's related but the problem with cp was when I also had Nautilus open and the target directory was currently selected.

Part way through the copy that window grayed out.  Sometimes the cp was successful and sometimes the whole system froze (mouse pointer included).

I can't say that I saw cp fail in this way without Nautilus open and the target directory selected.

---

### Post by Arlanthir on 2008-06-13
My system continues running perfectly fine, only the copy itself takes (much) longer than expected. 
Nautilus predicts 10 minutes and takes one hour, those sort of things (arbitrary values here, not tested, but I think they're close enough O.o)!

---

### Post by unutbu on 2008-06-13
Please post the output of

```
sudo hdparm -cudagiI /dev/sda
```
(Substitute the correct device name of your hard drive if it is not /dev/sda).

This will give us a lot of output regarding your hard drive. I am not an expert on what it all means, but there may be something we recognize in there, which if changed may speed up the performance. 

Also you may want to run 

```
sudo hdparm -Tt /dev/sda
```
This will give you another benchmark for how fast your system can read from disk. If we do find something to tweak with hdparm, then having these benchmark results will give you a measure of the performance gain (if any).

See 
[http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html](http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html)
for an example of the kind of tweaking I'm thinking of. 

Note: the commands above are all safe -- they are merely for gathering information. But please be careful with hdparm -- using it incorrectly can ask your hard drive to do things it wasn't meant to do and thereby damage your hard disk and/or corrupt your data. I would strongly recommend backing up all your data before trying any hdparm tweaks (unless you feel really confident you understand your drives capabilities and know what you're doing).

---

### Post by Arlanthir on 2008-06-14
Here goes:

sudo hdparm -cudagiI /dev/sda
```

/dev/sda:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 readahead     = 256 (on)
 geometry      = 9729/255/63, sectors = 156301488, start = 0

 Model=ST98823AS                               , FwRev=3.05    , SerialNo=            3PK0K780
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode


ATA device, with non-removable media
	Model Number:       ST98823AS                               
	Serial Number:      3PK0K780
	Firmware Revision:  3.05    
Standards:
	Supported: 7 6 5 4 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  156301488
	LBA48  user addressable sectors:  156301488
	device size with M = 1024*1024:       76319 MBytes
	device size with M = 1000*1000:       80026 MBytes (80 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Advanced power management level: 128
	Recommended acoustic management value: 254, current value: 0
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	DOWNLOAD_MICROCODE
	   *	Advanced Power Management feature set
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	IDLE_IMMEDIATE with UNLOAD
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	Phy event counters
	    	Device-initiated interface power management
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
Checksum: correct

```

sudo hdparm -Tt /dev/sda
```

/dev/sda:
 Timing cached reads:   2228 MB in  2.00 seconds = 1114.28 MB/sec
 Timing buffered disk reads:   50 MB in  3.05 seconds =  16.40 MB/sec

```

I have to be honest with you though, this doesn't seem like it needs tweaking, this seems like it needs fixing. Gutsy was alright without tweaking. And I don't like those ioctl errors on the first output :S

Thank you again for your help!

---

### Post by unutbu on 2008-06-14
Take a look at 
[http://ubuntuforums.org/showthread.php?t=61075](http://ubuntuforums.org/showthread.php?t=61075)
[http://ubuntuforums.org/showthread.php?t=30949&page=1&pp=10&highlight=enable+DMA](http://ubuntuforums.org/showthread.php?t=30949&page=1&pp=10&highlight=enable+DMA)

It looks like the problem is DMA is not enabled.
> 
/dev/sda:
 Timing cached reads:   2228 MB in  2.00 seconds = 1114.28 MB/sec
 **Timing buffered disk reads:   50 MB in  3.05 seconds =  16.40 MB/sec**
Your cached reads seem right quick, but your buffered disk reads seem to be rather slow.

Do you happen to have an AMD cpu? If so, the above threads seem to be saying you need to add

amd74xx 

to your /etc/modules. Do not do this unless you have an AMD cpu. 

In any case, what I've gathered so far from the threads is that you need to add the right module driver for your hard drive, and then enable DMA.

---

### Post by Arlanthir on 2008-06-14
In one of the threads:

[QUOTE=mlord]
If your disk is showing up as /dev/sda, then DMA is already enabled. No need to fiddle with it.

-ml
(hdparm author)[/QUOTE]

So... what should I do? :S

Regarding the CPU, no, it's not AMD.

How can I get a hardware listing?

---

### Post by unutbu on 2008-06-14
```
sudo lshw
```
will give you info about your hardware.
There is also System>Preferences>Hardware Information.

---

### Post by unutbu on 2008-06-14
Please post 
```

lsmod | grep ata
dmesg | grep ata
```

---

### Post by Arlanthir on 2008-06-14
lsmod | grep ata
```

ata_generic             8324  0 
pata_acpi               8320  0 
ata_piix               19588  1 
libata                159344  4 ata_generic,pata_acpi,ahci,ata_piix
scsi_mod              151436  6 sbp2,sg,sr_mod,sd_mod,usb_storage,libata

```

dmesg | grep ata
```

[    0.000000] ACPI: SSDT 3FE8C1AC, 020A (r1 SataRe SataAhci     1000 INTL 20060217)
[   10.324464] Memory: 1025904k/1047040k available (2177k kernel code, 20492k reserved, 1006k data, 368k init, 129536k highmem)
[   10.324490]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   11.352838] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[   23.441883] libata version 3.00 loaded.
[   23.877398] ata_piix 0000:00:1f.1: version 2.12
[   23.877661] scsi0 : ata_piix
[   23.878646] scsi1 : ata_piix
[   23.879411] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1880 irq 14
[   23.879417] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
[   24.197093] ata1.00: ATAPI: HL-DT-ST DVDRAM GMA-4082N, HQ04, max MWDMA2
[   24.368767] ata1.00: configured for MWDMA2
[   24.368859] ata2: port disabled. ignoring.
[   24.806930] ata3: SATA max UDMA/133 abar m1024@0xd2404400 port 0xd2404500 irq 219
[   24.806936] ata4: SATA max UDMA/133 abar m1024@0xd2404400 port 0xd2404580 irq 219
[   24.806942] ata5: SATA max UDMA/133 abar m1024@0xd2404400 port 0xd2404600 irq 219
[   24.806948] ata6: SATA max UDMA/133 abar m1024@0xd2404400 port 0xd2404680 irq 219
[   24.975201] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   24.976208] ata3.00: ATA-7: ST98823AS, 3.05, max UDMA/100
[   24.976214] ata3.00: 156301488 sectors, multi 16: LBA48 
[   24.979933] ata3.00: configured for UDMA/100
[   25.044458] ata4: SATA link down (SStatus 0 SControl 0)
[   25.109897] ata5: SATA link down (SStatus 0 SControl 0)
[   25.175686] ata6: SATA link down (SStatus 0 SControl 0)
[   26.082857] EXT3-fs: mounted filesystem with ordered data mode.

```

I didn't know if I was supposed to unmount all external stuff, so, I did it with all mounted (I was copying files). I really hope that means a lot more to you than it does to me :P

---

### Post by Arlanthir on 2008-06-18
I've noticed that more people have the same problem, and it's not with nautilus.
Can anyone provide a clear fix to this? I've read the cdrom thread but don't know how to proceed with a HDD :S

---

### Post by unutbu on 2008-06-18
Please post 
```

sudo lshw -C cpu
sudo lshw -C disk
```

I wonder if these lines might be clues:

```
[   23.879411] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1880 irq 14
[   23.879417] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
[   24.197093] ata1.00: ATAPI: HL-DT-ST DVDRAM GMA-4082N, HQ04, max MWDMA2
[   24.368767] ata1.00: configured for MWDMA2
**[   24.368859] ata2: port disabled. ignoring.**
[   24.806930] ata3: SATA max UDMA/133 abar m1024@0xd2404400 port 0xd2404500 irq 219
[   24.806936] ata4: SATA max UDMA/133 abar m1024@0xd2404400 port 0xd2404580 irq 219
[   24.806942] ata5: SATA max UDMA/133 abar m1024@0xd2404400 port 0xd2404600 irq 219
[   24.806948] ata6: SATA max UDMA/133 abar m1024@0xd2404400 port 0xd2404680 irq 219
[   24.975201] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   24.976208] ata3.00: ATA-7: ST98823AS, 3.05, max UDMA/100
[   24.976214] ata3.00: 156301488 sectors, multi 16: LBA48 
[   24.979933] ata3.00: configured for UDMA/100
[B][   25.044458] ata4: SATA link down (SStatus 0 SControl 0)
[   25.109897] ata5: SATA link down (SStatus 0 SControl 0)
[   25.175686] ata6: SATA link down (SStatus 0 SControl 0)[/B]
[   26.082857] EXT3-fs: mounted filesystem with ordered data mode.
```

---

### Post by Arlanthir on 2008-06-19
I'm going to try the cdrom fix anyway, just for the heck of desperation.
This PC is going to repair sooner or later because of overheating issues so, all backups are done =X
**Edit:** No I'm not, I don't even have the IDE modules there -_-


/etc/modules

```
fuse
lp
sbp2

```


sudo lshw -C cpu

```
  *-cpu:0                 
       description: CPU
       product: Genuine Intel(R) CPU           T2400  @ 1.83GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: 6.14.8
       serial: 0000-06E8-0000-0000-0000-0000
       slot: U1
       size: 1833MHz
       capacity: 1833MHz
       width: 32 bits
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor vmx est tm2 xtpr cpufreq
       configuration: id=0
     *-logicalcpu:0
          description: Logical CPU
          physical id: 0.1
          width: 32 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 0.2
          width: 32 bits
          capabilities: logical
  *-cpu:1
       physical id: 1
       bus info: cpu@1
       version: 6.14.8
       serial: 0000-06E8-0000-0000-0000-0000
       size: 1833MHz
       capacity: 1833MHz
       capabilities: vmx ht cpufreq
       configuration: id=0
     *-logicalcpu:0
          description: Logical CPU
          physical id: 0.1
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 0.2
          capabilities: logical
```


sudo lshw -C disk

```
  *-cdrom                 
       description: DVD-RAM writer
       product: DVDRAM GMA-4082N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: HQ04
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
  *-disk
       description: ATA Disk
       product: ST98823AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.05
       serial: 3PK0K780
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=b308b308
  *-disk
       description: SCSI Disk
       product: 3200BEV External
       vendor: WD
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       version: 1.04
       serial: WD-WXE108L03694
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=4 signature=5b6ac646

```

---

### Post by unutbu on 2008-06-19
Arlanthir, 

I wonder if using "combined mode" (a BIOS IDE mode) with libata is causing the problem. See [http://linux-ata.org/faq.html#combined](http://linux-ata.org/faq.html#combined). They recommend in this situation to enter your BIOS menu and change your IDE mode from "legacy" or "combined" to "AHCI" (recommended), "RAID" or "native". 

There might be other BIOS IDE configuration options like "Enhanced Mode Support On" or "P-ATA + S-ATA". 

I don't know what each of these options mean, but it may be worth trying each possible option and seeing if there is any improvement in the benchmarks

```

sudo hdparm -Tt /dev/sda
sudo hdparm -Tt /dev/sdb
```

---

### Post by Arlanthir on 2008-06-19
My BIOS is rather simple, here's a "screenshot" of the current configuration :S

---

### Post by unutbu on 2008-06-19
Please post

```
lsmod | grep ide
uname -r

```

---

### Post by Arlanthir on 2008-06-19
```

arlanthir@Icarus:~$ lsmod | grep ide
video                  19856  5 
output                  4736  1 video
arlanthir@Icarus:~$ uname -r
2.6.24-19-generic

```

I think this isn't what you were hoping for :P

---

### Post by unutbu on 2008-06-19
Yeah, you're right -- that wasn't the output I was hoping for. I don't know the answer, but I am still searching.

You might want to start a new thread with a more accurate title -- perhaps that will attract the right type of reader. Maybe 

"Slow hard drive even though DMA is enabled"

or something of that sort.

---

### Post by Arlanthir on 2008-06-20
How do you know DMA is enabled? :S Yeah, I think that's a good idea too, but I want to get the facts straight.. :(

Thank you for your help!

---

### Post by unutbu on 2008-06-20
Per you post #13, I'm inclined to believe mlord when he says DMA is enabled if your drive shows up as /dev/sda (rather than /dev/hda). Also 

From dmesg:
> 
[   24.368767] ata1.00: configured for MWDMA2
[   24.979933] ata3.00: configured for UDMA/100

ata1 is your PATA (internal) drive
ata3 is your SATA (external) drive.

I'm still trying to figure out how fast MWDMA2 is.

I think there is some room for improvement here -- dmesg says
ata1's maximum mode is UDMA/100 (I'm guessing that might be better than MWDMA2, but I'm not sure). and ata3's maximum mode is UDMA/133, which should be better than UDMA/100.

I assumed you have already tried 

```

hdparm -d1 /dev/sda
hdparm -d1 /dev/sdb

```
There is a way to set the transfer mode using hdparm with the -X flag, but I'm afraid to suggest it because mlord's man page scares me:

```

-X     Set the IDE transfer mode for newer (E)IDE/ATA drives.  This is typically
       used  in combination with -d1 when enabling DMA to/from a drive on a sup&#8208;
       ported interface chipset, where -X mdma2 is used to select multiword  DMA
       mode2  transfers  and -X sdma1 is used to select simple mode 1 DMA trans&#8208;
       fers.  With systems which support UltraDMA burst  timings,  -X  udma2  is
       used  to  select  UltraDMA  mode2  transfers  [B](you´ll need to prepare the
       chipset for UltraDMA beforehand)[/B].  Apart from that, use of this  flag  is
       seldom  necessary  since  most/all  modern  IDE  drives  default to their
       fastest PIO transfer mode at power-on.  [B]Fiddling with this  can  be  both
       needless and risky.[/B]  On drives which support alternate transfer modes, -X
       can be used to switch the mode of the drive only.  [B]Prior to changing  the
       transfer mode, the IDE interface should be jumpered or programmed (see -p
       flag) for the new mode setting to prevent loss and/or corruption of data.
       Use  this  with  extreme  caution![/B]  For the PIO (Programmed Input/Output)
       transfer modes used by Linux, this value is simply the desired  PIO  mode
       number plus 8.  Thus, a value of 09 sets PIO mode1, 10 enables PIO mode2,
       and 11 selects PIO mode3.  Setting 00 restores the drive´s "default"  PIO
       mode,  and  01  disables IORDY.  For multiword DMA, the value used is the
       desired DMA mode number plus 32.  for UltraDMA, the value is the  desired
       UltraDMA mode number plus 64.

```

---

### Post by Arlanthir on 2008-06-20
I've been trying to set the DMA with those commands (and others more verbose) but the answer is always the same:

```
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

```

I'll post another thread in a while ;)

---

### Post by unutbu on 2008-06-20
According to [http://linux-ata.org/faq.html#old_ioctls](http://linux-ata.org/faq.html#old_ioctls),
the driver you are currently using (libata), does not implement all HDIO_xxx ioctls, such as HDIO_SET_DMA.
Unfortunately, it doesn't say what to do if you need to set it yourself.

Perhaps the solution is to use a different driver, or perhaps a boot-time kernel option.
I know there are a whole bunch of ata drivers in 
/lib/modules/2.6.24-19-generic/kernel/drivers/ata,
but I don't know enough yet to suggest to you what to try.

---

### Post by Arlanthir on 2008-06-20
New thread: [here!]("http://ubuntuforums.org/showthread.php?p=5227043")

---

