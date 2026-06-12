---
title: "Hardy LiveCD won't recognize hard drives"
date: 2008-06-02
forum: General Help
---

### Post by kernalsanders123 on 2008-06-02
I'm in an interesting bit of a jam, so here is the rundown:

My computer is currently running a dual installation, Windows on one drive, Ubuntu 7.10 on another, both SATA drives. I've been trying to shrink my Ubuntu partition via Gparted, but I have run into several stumbling blocks:

I am unable to use LiveCDs from versions 7.04 and earlier, since I am using a Nvidia Geforce 8800GT video card, which, from reading several threads, and my own experience, seem to have trouble with Ubuntu.

So, I naturally attempted to use a Hardy LiveCD, which brings me to my main problem: It boots without trouble. However, neither of my hard drives are recognized by Ubuntu, either in gnome, Gparted, or fdisk. Doing a bit of research, I noticed that one of the known Hardy bugs was about SATA drives not being detected in IDE mode, but it seemed to only apply to Dell computers, and I looked around my BIOS, but I didn't see any options concerning SATA and IDE. Also, both my current Ubuntu and Windows installations both detect my hard drives without any trouble.

I have also tried the standalone Gparted LiveCD, but the video would not work, also due to my 8800GT video card, I'm guessing.

In short, I'm wondering if anyone has had any trouble or luck in getting a Hardy LiveCD to recognize their SATA hard drives. Any help would be greatly appreciated.

(P.S. Sorry if my explanation is a bit lengthy, but I figure the more information available, the better.)

---

### Post by hal8000 on 2008-06-02
Do you have any optical (CD or DVD) drives on your computer and if yes are they SATA or IDE?

I found that my problems with libATA were down to shared IRQ's. I had 2 IDE drives on the same IDE cable and a DVD and CDROM again on the same IDE cable.
I bought a single SATA drive and removed a CDROM< I have have a single IDE hard drive on its own cable, a DVDwriter on its own IDE cable and a SATA HD and performance is great.
If this is not the case with the Hardy Live CD trypressing F6 and appending irqpoll to the boot prompt, you may get it to boot.

---

### Post by kernalsanders123 on 2008-06-02
I've got 2 SATA optical drives, both of which the LiveCD recognizes. As for irqpoll, I tried it, but the LiveCD still doesn't recognize my hard drives.

---

### Post by kernalsanders123 on 2008-06-05
bump?

---

### Post by Kernel_Krunch on 2008-06-05
> **kernalsanders123 said:**
> bump?

Ok, not really sure what your trying to do other then resize your ubuntu partition.  If that is all you want to do then use "Insert" a linux distro designed for system fixing.

I have the problem of the LiveCD detecting my IDE lol, I think Hardy lost support for some motherboard chipsets... VIA for me, an attribute walk shows some werd "pata_via" node... Although a distro upgrade works fine i guess.

---

### Post by kernalsanders123 on 2008-06-05
I'd use my existing install, but the partition I'm trying to resize is the partition Ubuntu is installed on. As for using a LiveCD, I'm  kind of the victim of a double whammy. I can't get any versions prior to and including 7.10 to boot properly, which, after doing some research, I attribute to my 8800GT video card. I've done some looking around, and tried several possible solutions, but none of them work.

And, when I try the Hardy LiveCD, none of my SATA drives are recognized. Some threads report Dell users having a similar problem, which was fixed by switching their SATA mode from IDE to RAID. I checked my BIOS, but the only option I found was to set up RAID on my computer, which I didn't try, since I'm pretty sure would involve wiping my hard drive, unless I'm wrong, which is very possible.

Another solution that I saw involved adding "all_generic_ide" to the GRUB loading screen, but since I'm using a LiveCD, there is no GRUB screen to my knowledge.

I've also tried Debian and DSL LiveCDs, but to no avail, also having to do with my video card, I believe.

So, that is my situation as far as I can tell. If I have overlooked any obvious solutions, I apologize, as I am still a newbie in many respects.

---

### Post by kernalsanders123 on 2008-06-20
bump?

---

### Post by louieb on 2008-06-20
I've had trouble with the GParted live CD in the past. Might try the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") its what I use now. It has GParted on it. The [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic") also has GParted on it. Don't know why your having trouble with the hardy CD not seeing your drives. A bad CD is the only reason I can think of.

---

### Post by kernalsanders123 on 2008-06-21
I'm pretty sure the CD is good, since I tested it on my Thinkpad, and the CD recognized the hard drive just fine, so I'm pretty sure it's my hardware/hardware settings.

---

### Post by kernalsanders123 on 2008-06-22
Ok, I've been doing some more poking around, and I found some related output from running the dmesg command from my LiveCD. Here's an excerpt of what I believe is the applicable information:

```
   26.712873] sata_nv 0000:00:07.0: version 3.5
[   26.712887] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
[   26.712890] sata_nv 0000:00:07.0: Using ADMA mode
[   26.713067] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   26.714655] scsi0 : sata_nv
[   26.714850] scsi1 : sata_nv
[   26.715023] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd400 irq 20
[   26.715026] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd408 irq 20
[   26.918124] usb 1-6: configuration #1 chosen from 1 choice
[   26.930159] usbcore: registered new interface driver hiddev
[   26.936145] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb1/1-6/1-6:1.0/input/input2
[   26.960928] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:02.0-6
[   26.960937] usbcore: registered new interface driver usbhid
[   26.960940] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   27.179562] ata: SEMB device ignored
[   27.179570] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   27.646789] ata: SEMB device ignored
[   27.646792] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   27.646832] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 23
[   27.646836] sata_nv 0000:00:08.0: Using ADMA mode
[   27.647024] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   27.647129] scsi2 : sata_nv
[   27.647186] scsi3 : sata_nv
[   27.647346] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc000 irq 23
[   27.647348] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc008 irq 23
[   28.114035] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   28.277853] ata3.00: ATAPI: SONY    DVD RW AW-G170S, 1.72, max UDMA/66
[   28.449571] ata3.00: configured for UDMA/66
[   28.916734] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   29.096526] ata4.00: ATAPI: LITE-ON COMBO SHC-52S7K, VK03, max UDMA/100
[   29.284228] ata4.00: configured for UDMA/100
[   29.285752] scsi 2:0:0:0: CD-ROM            SONY     DVD RW AW-G170S  1.72 PQ: 0 ANSI: 5
[   29.285758] ata3: bounce limit 0xFFFFFFFF, segment boundary 0xFFFF, hw segs 127
[   29.286870] scsi 3:0:0:0: CD-ROM            LITE-ON  COMBO SHC-52S7K  VK03 PQ: 0 ANSI: 5
[   29.286874] ata4: bounce limit 0xFFFFFFFF, segment boundary 0xFFFF, hw segs 127
[   29.287015] pata_amd 0000:00:06.0: version 0.3.10
[   29.287067] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   29.287700] scsi4 : pata_amd
[   29.287977] scsi5 : pata_amd
[   29.288506] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
[   29.288508] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
[   29.294863] Driver 'sr' needs updating - please use bus_type methods
[   29.298656] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   29.298660] Uniform CD-ROM driver Revision: 3.20
[   29.298694] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   29.306927] sr1: scsi3-mmc drive: 0x/52x writer cd/rw xa/form2 cdda tray
[   29.306976] sr 3:0:0:0: Attached scsi CD-ROM sr1
[   29.310268] sr 2:0:0:0: Attached scsi generic sg0 type 5
[   29.310287] sr 3:0:0:0: Attached scsi generic sg1 type 5
[   30.635847] ISO 9660 Extensions: Microsoft Joliet Level 3
[   30.676032] ISO 9660 Extensions: RRIP_1991A
```

I noticed that it recognizes ata3 and ata4 as my CD drives, and it recognizes ata1 and ata2 as SATA devices, but it doesn't specify. Also, I noticed that after ata1 and ata2, there are entries that state: SEMB device ignored. I tried googling it, but I couldn't really find any useful info about it. Anyone have any idea what it means, and if so, could it be why my hard drives aren't being recognized?

As for other possible solutions, I've tried adding "all_generic_ide", "irqpoll", "noapic", "nolapic", "acpi=off",  and "pci=noacpi" in various combinations, but no dice there.

---

### Post by unutbu on 2008-06-22
Please boot from your hard drive and post the output of

```
dmesg | grep ata
```

---

### Post by kernalsanders123 on 2008-06-22
Here's the results of dmesg | grep ata from my current Gutsy install on my hard drive:

```
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[   15.755474] Memory: 2056116k/2097088k available (2274k kernel code, 40584k reserved, 1185k data, 300k init)
[   19.279552] libata version 2.21 loaded.
[   21.149114] sata_nv 0000:00:07.0: version 3.4
[   21.149503] sata_nv 0000:00:07.0: Using ADMA mode
[   21.150183] scsi0 : sata_nv
[   21.150396] scsi1 : sata_nv
[   21.150581] ata1: SATA max UDMA/133 cmd 0xffffc20000aa8480 ctl 0xffffc20000aa84a0 bmdma 0x000000000001d400 irq 20
[   21.150585] ata2: SATA max UDMA/133 cmd 0xffffc20000aa8580 ctl 0xffffc20000aa85a0 bmdma 0x000000000001d408 irq 20
[   21.619976] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   21.637831] ata1.00: ATA-7: WDC WD1600JS-62MHB5, 10.02E02, max UDMA/133
[   21.637834] ata1.00: 312581808 sectors, multi 16: LBA48 
[   21.648126] ata1.00: configured for UDMA/133
[   22.115201] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   22.138206] ata2.00: ATA-7: WDC WD1600JS-62MHB5, 10.02E02, max UDMA/133
[   22.138209] ata2.00: 312581808 sectors, multi 16: LBA48 
[   22.147326] ata2.00: configured for UDMA/133
[   22.147420] ata1: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   22.147807] ata2: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   22.148434] sata_nv 0000:00:08.0: Using ADMA mode
[   22.148669] scsi2 : sata_nv
[   22.148925] scsi3 : sata_nv
[   22.149102] ata3: SATA max UDMA/133 cmd 0xffffc20000aaa480 ctl 0xffffc20000aaa4a0 bmdma 0x000000000001c000 irq 23
[   22.149107] ata4: SATA max UDMA/133 cmd 0xffffc20000aaa580 ctl 0xffffc20000aaa5a0 bmdma 0x000000000001c008 irq 23
[   22.618415] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   22.782231] ata3.00: ATAPI: SONY    DVD RW AW-G170S, 1.72, max UDMA/66
[   22.953962] ata3.00: configured for UDMA/66
[   23.421159] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   23.600952] ata4.00: ATAPI: LITE-ON COMBO SHC-52S7K, VK03, max UDMA/100
[   23.788656] ata4.00: configured for UDMA/100
[   23.789518] ata3: bounce limit 0xFFFFFFFF, segment boundary 0xFFFF, hw segs 127
[   23.791081] ata4: bounce limit 0xFFFFFFFF, segment boundary 0xFFFF, hw segs 127
[   24.183871] EXT3-fs: mounted filesystem with ordered data mode.

```

And here is the same results from using a LiveCD, if it will be of any help:


```
[   57.757787] sata_nv 0000:00:07.0: version 3.5
[   57.757806] sata_nv 0000:00:07.0: Using ADMA mode
[   57.758103] scsi2 : sata_nv
[   57.758345] scsi3 : sata_nv
[   58.693456] sata_nv 0000:00:08.0: Using ADMA mode
[   58.693735] scsi4 : sata_nv
[   58.693982] scsi5 : sata_nv
ubuntu@ubuntu:~$ dmesg | grep ata
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[   53.799238] Memory: 2054824k/2097088k available (2466k kernel code, 41876k reserved, 1309k data, 316k init)
[   56.607949] libata version 3.00 loaded.
[   57.424463] pata_amd 0000:00:06.0: version 0.3.10
[   57.424622] scsi0 : pata_amd
[   57.424666] scsi1 : pata_amd
[   57.425137] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
[   57.425139] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
[   57.757787] sata_nv 0000:00:07.0: version 3.5
[   57.757806] sata_nv 0000:00:07.0: Using ADMA mode
[   57.758103] scsi2 : sata_nv
[   57.758345] scsi3 : sata_nv
[   57.758499] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd400 irq 22
[   57.758502] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd408 irq 22
[   58.226075] ata: SEMB device ignored
[   58.226084] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   58.693323] ata: SEMB device ignored
[   58.693326] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   58.693456] sata_nv 0000:00:08.0: Using ADMA mode
[   58.693735] scsi4 : sata_nv
[   58.693982] scsi5 : sata_nv
[   58.694136] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc000 irq 21
[   58.694138] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc008 irq 21
[   59.160570] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   59.324384] ata5.00: ATAPI: SONY    DVD RW AW-G170S, 1.72, max UDMA/66
[   59.496105] ata5.00: configured for UDMA/66
[   59.963270] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   60.143054] ata6.00: ATAPI: LITE-ON COMBO SHC-52S7K, VK03, max UDMA/100
[   60.330751] ata6.00: configured for UDMA/100
[   60.332432] ata5: bounce limit 0xFFFFFFFF, segment boundary 0xFFFF, hw segs 127
[   60.333844] ata6: bounce limit 0xFFFFFFFF, segment boundary 0xFFFF, hw segs 127

```

---

### Post by unutbu on 2008-06-23
When you boot Gutsy from the HD, it appears sata_nv claims scsi0 and scsi1:
```
scsi0 : sata_nv
scsi1 : sata_nv
ata1: SATA max UDMA/133 cmd 0xffffc20000aa8480 ctl 0xffffc20000aa84a0 bmdma 0x000000000001d400 irq 20
ata2: SATA max UDMA/133 cmd 0xffffc20000aa8580 ctl 0xffffc20000aa85a0 bmdma 0x000000000001d408 irq 20
ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata1.00: ATA-7: WDC WD1600JS-62MHB5, 10.02E02, max UDMA/133
ata1.00: 312581808 sectors, multi 16: LBA48 
ata1.00: configured for UDMA/133
ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata2.00: ATA-7: WDC WD1600JS-62MHB5, 10.02E02, max UDMA/133
ata2.00: 312581808 sectors, multi 16: LBA48 
ata2.00: configured for UDMA/133
ata1: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
ata2: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61

```

But when you boot from Hardy LiveCD, pata_amd claims scsi0 and scsi1, and your hard drives ultimately get ignored:
```
pata_amd 0000:00:06.0: version 0.3.10
scsi0 : pata_amd
scsi1 : pata_amd
ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
ata: SEMB device ignored
ata: SEMB device ignored
```
I'm not sure how to tell the LiveCD to not use pata_amd.

---

### Post by kernalsanders123 on 2008-06-24
Ok, another update: I dug up an old 173MB IDE Western Digital hard drive, which the Hardy LiveCD recognized without a hitch. Not sure if that really helps to narrow it down at all, but I figured it's worth noting. I was also thinking that the brand might be an issue. I myself have never had any problems with Western Digital, but you never know. Anyone else have any troubles with Hardy and Western Digital hard drives?

---

### Post by unutbu on 2008-06-24
I'm sorry I don't know a better solution for you kernalsanders123. I hear Knoppix is very good at detecting hardware. Maybe give that one a try.

By the time we're through with you, you will have a shelf full of Linux distros!

---

### Post by kernalsanders123 on 2008-06-24
Funny you should mention that. I've actually had to try several distros, apparently many of them have problems with my 8800GT video card, since I've tried Knoppix, Finnix, Gparted, Debian, Gutsy, and Feisty LiveCDs, and none of them worked. They all worked fine on my old video card, an ATI X1950 Pro, but the only Live distros I've been able to get to work on my machine is Hardy, which won't read my drives, and Mepis, which works fine. I have used that for repartitioning, but my concern is being able to use the Hardy LiveCD, since I'd like to be able to have the option to reinstall, in case any attempt at upgrading might go haywire.

---

### Post by unutbu on 2008-06-24
If you could alter the Hardy LiveCD, (as though it were a linux installation on a partition), I think the solution is similar to these:

[http://ubuntuforums.org/showpost.php?p=4218596&postcount=9](http://ubuntuforums.org/showpost.php?p=4218596&postcount=9)
[http://ubuntuforums.org/showpost.php?p=4218717&postcount=2](http://ubuntuforums.org/showpost.php?p=4218717&postcount=2)
[http://ubuntuforums.org/showpost.php?p=5096657&postcount=2](http://ubuntuforums.org/showpost.php?p=5096657&postcount=2)

Namely, you edit /etc/initramfs-tools/modules to contain

```
sata_nv
blacklist pata_amd
```
and then run ```

sudo update-initramfs -u
```

These commands I think will allow sata_nv to load before pata_amd. This *might* work if you could roll your own custom Hardy LiveCD, but I'm not familiar with how to do that.

---

### Post by unutbu on 2008-06-25
I happened to be reading 
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94981](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94981)
when I thought of you. Near the end there is a report from Mantas Kriau&#269;i&#363;nas that booting with boot option

```
generic.all_generic_ide=1
```

was necessary make Ubuntu 7.04 LiveCD recognize his drive. I know your situation is a little different, and you've already tried all_generic_ide, but perhaps not exactly this way. Anyway, I thought I'd pass it on; it's maybe worth a shot.

---

### Post by kernalsanders123 on 2008-06-26
Ok, update as follows:

I tried a custom install with satanv and blacklist pata_amd, and I also tried generic.all_generic_ide=1, no dice on either.

However, I found semi-related forum about someone's troubles with SATA on a Gigabyte motherboard. My mobo's an Abit, but they both use the Nforce 4 chipset, and one person's post stated that SATA II ports are powered by the Nforce 4 chipset, while the SATA I drivers are powered by a "Silicon Image 3114 driver". Full thread [here]("http://icrontic.com/forum/showthread.php?t=25791")

I then noticed that my dmesg output reads my CD drives as SATA I drives, due to the speed being listed as 1.5GB/sec. I know that my hard drives are SATA II, so if these are similar problems, might there be a different module I would need, since the sata_nv module is for nvidia chipsets? Just a thought, I might not even be in the same ballpark, so, if anyone might have any thoughts for or against, please do tell.

---

### Post by unutbu on 2008-06-26
Please post
```
lspci -nn
```

---

### Post by kernalsanders123 on 2008-06-26
```
custom@custom:~$ lspci -nn
00:00.0 Memory controller [0580]: nVidia Corporation CK804 Memory Controller [10de:005e] (rev a3)
00:01.0 ISA bridge [0601]: nVidia Corporation CK804 ISA Bridge [10de:0050] (rev a3)
00:01.1 SMBus [0c05]: nVidia Corporation CK804 SMBus [10de:0052] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation CK804 USB Controller [10de:005a] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation CK804 USB Controller [10de:005b] (rev a3)
00:04.0 Multimedia audio controller [0401]: nVidia Corporation CK804 AC'97 Audio Controller [10de:0059] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation CK804 IDE [10de:0053] (rev f2)
00:07.0 IDE interface [0101]: nVidia Corporation CK804 Serial ATA Controller [10de:0054] (rev f3)
00:08.0 IDE interface [0101]: nVidia Corporation CK804 Serial ATA Controller [10de:0055] (rev f3)
00:09.0 PCI bridge [0604]: nVidia Corporation CK804 PCI Bridge [10de:005c] (rev a2)
00:0a.0 Bridge [0680]: nVidia Corporation CK804 Ethernet Controller [10de:0057] (rev a3)
00:0b.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0c.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0d.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0e.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
05:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8800 GT [10de:0611] (rev a2)

```

---

### Post by kernalsanders123 on 2008-06-26
Hmmm, found a bit of a discrepancy, if you want to call it that. I ran lshw on both my LiveCD and my install already on my HD.

Here's what my existing install lists for SATA controllers:

```
module=amd74xx
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
```

and here's what my LiveCD gives me for SATA controllers:

```
module=pata_amd
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi2
          logical name: scsi3
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-cdrom:0
             description: DVD-RAM writer
             product: DVD RW AW-G170S
             vendor: SONY
             physical id: 0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 1.72
             serial: [SONY    DVD RW AW-G170S 1.72 Dec14,2006
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=open
        *-cdrom:1
             description: DVD reader
             product: COMBO SHC-52S7K
             vendor: LITE-ON
             physical id: 1
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/dvd1
             logical name: /dev/scd1
             logical name: /dev/sr1
             logical name: /media/cdrom
             version: VK03
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom1
                logical name: /media/cdrom
                configuration: mount.fstype=iso9660
```

3 things I noticed:

1. My LiveCD uses pata_amd even though I blacklisted it under /etc/initramfs-tools/modules.

2. My existing install doesn't even use pata_amd to begin with, is it something introduced with Hardy?

3. One of the SATA controllers is listed as module amd74xx, which isn't present in the LiveCD.

So, by my guess, my comp seems to be using several different modules for SATA controllers. Might this be a bit of an issue? (As a disclaimer, I still consider myself a n00b in the ways of Linux, so this is the results of my own limited knowledge and deductions.)

---

### Post by unutbu on 2008-06-26
> My LiveCD uses pata_amd even though I blacklisted it under /etc/initramfs-tools/modules.

Blacklisting modules in /etc/initramfs-tools/modules does not prevent the module from eventually getting loaded. It only delays it. This can be helpful to some users, because it may give a different module a chance to claim control of a device. To blacklist it fully, you need to add the module name to /etc/modprobe.d/blacklist in addition to /etc/initramfs-tools/modules.

I'm only just learning about initramfs myself, but it appears that it loads a mini operating system (/boot/initrd.img-*) before handing off control to the kernel (/boot/vmlinuz-*).
The command "sudo update-initramfs -u" reads /etc/initramfs-tools/modules and modifies /boot/initrd.img-`uname -r` accordingly. So by blacklisting modules in /etc/initramfs-tools/modules you are only affecting initrd.img. The kernel which gains control later can also load modules, which is why you are seeing pata_amd even though you blacklisted it under /etc/initramfs-tools/modules.

If you can make another custom Hardy CD, 
blacklisting pata_amd in both initramfs-tools/modules and /etc/modprobe.d/blacklist, and adding amd74xx to /etc/modules,... maybe that is worth a shot?

---

### Post by unutbu on 2008-06-26
When you downloaded the Hardy LiveCD, did you download the 64bit AMD version?

brons2's lspci looks similar to yours:
[http://ubuntuforums.org/showthread.php?t=841811](http://ubuntuforums.org/showthread.php?t=841811)
He had a graphics problem, but not your hard drive recognition problem. I wonder if the 64bit AMD version uses amd74xx automatically.

---

### Post by kernalsanders123 on 2008-06-26
Tried blacklisting pata_amd, and adding amd74xx to /etc/modules, but no luck, AMD74XX doesn't show up in lshw output, either:

   ```
*-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi2
          logical name: scsi3
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-cdrom:0
             description: DVD-RAM writer
             product: DVD RW AW-G170S
             vendor: SONY
             physical id: 0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 1.72
             serial: [SONY    DVD RW AW-G170S 1.72 Dec14,2006
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=open
        *-cdrom:1
             description: DVD reader
             product: COMBO SHC-52S7K
             vendor: LITE-ON
             physical id: 1
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/dvd1
             logical name: /dev/scd1
             logical name: /dev/sr1
             logical name: /media/cdrom
             version: VK03
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom1
                logical name: /media/cdrom
                configuration: mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted
```

Perhaps if I were to try some of the boot options I tried earlier, or would that just be wishful thinking?

---

### Post by kernalsanders123 on 2008-06-27
OK, did some more research, and according to Nvidia's website, the amd74xx driver is for IDE drives. I also considered trying the ahci driver, but after more research, I found that my Nforce 4 chipset isn't ahci compatible. So, that leaves me with the sata_nv driver to mess with.

---

### Post by kernalsanders123 on 2008-06-28
Out of curiosity, does anyone know if they did some major change or something to the way Ubuntu handles SATA drives? I ask because, glancing at this forum and some others, it seems as though quite a few people are encountering a problem similar to mine, leading me to believe that in some instances, it seems as though Ubuntu's SATA support has gone to h*** in a handbasket. I've been using feisty and gutsy for the last 2 years or so, and I had nary a peep from them regarding SATA drives. Now, with Hardy, all it seems to be doing is stonewalling me.

---

### Post by cariboo on 2008-06-28
Check and see if there is an AHCI setting in your bios, I've got an MSI MB with the nvidia chipset, I had to enable ahci to get my 3 sata drives recognized along with my pata hdd and dvd/rw drive.

Jim

---

### Post by kernalsanders123 on 2008-06-28
My mobo has a nForce 4 chipset, which, after some research, apparently does not support ahci. As far as BIOS options are concerned, I can enable or disable IDE 1 and 2, IDE DMA transfer access, or the onchip sata controllers. Also, for each individual device, I can enable or disable the extended IDE drive, and set access mode to large or auto.

---

### Post by unutbu on 2008-06-28
> my concern is being able to use the Hardy LiveCD, since I'd like to be able to have the option to reinstall, in case any attempt at upgrading might go haywire.

Maybe we have been banging our heads against the wrong wall. Why not make a clone ([http://www.clonezilla.org/](http://www.clonezilla.org/)) of your current setup instead?

---

### Post by kernalsanders123 on 2008-06-28
I've actually been considering that. I've been meaning to get a bigger hard drive for backup purposes. My only concern is that if I upgrade, I'll get the same problems I'm having with the LiveCD i.e., no SATA hard drives. I could then restore, but I'd still be stuck with an older version, and a machine that can't upgrade properly.

---

### Post by unutbu on 2008-06-28
Given the problem you are experiencing, I would not try a software upgrade. The safe way -- and in your case the only sensible way -- is to create a new partition (about 10GB should suffice) and install your next OS in there. That is the only way you can test out the next OS without losing your current setup. 

Of course, this point is worthless until you find a LiveCD that installs...

---

### Post by kernalsanders123 on 2008-06-28
I have noticed that my current install is using libata version 2.21, and sata_nv version 3.4. My LiveCD, however, is using libata version 3.0, and sata_nv version 3.5. Might the newer drivers be buggy? And, if so, is it possible to use the older drivers from Gutsy on a Hardy LiveCD? Just a thought.

---

### Post by unutbu on 2008-06-28
Maybe you can create a custom Hardy LiveCD which uses Gutsy's libata version 2.21, and sata_nv version 3.4:

See:
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) [http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

### Post by kernalsanders123 on 2008-06-29
Seems as though those 2 drivers are part of the kernel. I'm guessing things get hairy from that point on. I personally have never messed with the kernel, outside of updating it via Ubuntu's update manager. Searching for libata and sata_nv, they turn up in modules located in:

/lib/modules/2.6.24-19-generic/kernel/drivers/ata/libata.ko

/usr/src/linux-headers-2.6.24-19-generic/include/linux/libata.h

/usr/src/linux-headers-2.6.24-19/include/linux/libata.h

/lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_nv.ko

So, is it just a matter of copying the existing files from my Gutsy install over to my Hardy install and making a LiveCD out of it? (I have a working Hardy install on my laptop, which I'm making custom LiveCDs out of).

I'm assuming it's not that simple. From what little I know about the kernel, I usually hear of it needing to be recompiled after altering it, which I haven't the foggiest on how to do, either editing or recompiling.

So, any guidance anyone might have would be greatly appreciated.

---

### Post by kernalsanders123 on 2008-07-02
Bump with a new question: The moment Ubuntu seems to drop my drives is when it gets to "SEMB device ignored". Searching via multiple search engines, it seems as though I'm the only one on the internet that has ever gotten that message. Has anyone else ever encountered it, or have any idea what it means, or how to correct it?

---

### Post by kernalsanders123 on 2008-08-07
p.s. I know I mentioned it earlier, but I noticed that the sata_nv driver works fine under my current Gutsy install, but both Hardy and Intrepid use version 3.5, which seems to have ceased working for my hard drives. Does anyone know anything about what may have changed between the different versions?

---

### Post by kernalsanders123 on 2008-08-13
Another update:
After doing some digging regarding the latest kernel versions and my nForce 4 chipset, I found that Gentoo might also have the same kind of problem here:

[http://gentoo-wiki.com/SATA#SiI_3114_SATA_.2F_CK804_Nvidia_Serial_ATA](http://gentoo-wiki.com/SATA#SiI_3114_SATA_.2F_CK804_Nvidia_Serial_ATA)

The article says to enable ```
CONFIG_SATA_NV=y
```. Also, at the very bottom of the page, under "nForce Serial ATA, it says to enable SCSI support with these commands:

```
CONFIG_SCSI=y
CONFIG_BLK_DEV_SD=y
```

Reading the rest of the article, it seems that these are commands you set when compiling the kernel yourself. Can anyone confirm or deny this? I'm not sure myself, as I have never touched the kernel itself, outside of updating it via the update manager.  However, part of me doubts if this would help, as my CD drives are detected by the Hardy LiveCD just fine, but not my hard drives.

p.s.

Via the kernel newbies webiste, I found a list of changes made for kernel version 2.6.24, one of which included enabling HPET on the nForce 4 chipset. 

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=d79a5f80dc1153d3f637dfcf3808066414fbb51a](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=d79a5f80dc1153d3f637dfcf3808066414fbb51a)

All I know about HPET is that it has something to do with being a timer or something, but it does apply to my sata driver, and they even apparently tested it on the same type of mobo I have, an Abit KN9. If this has anything to do with my SATA issues, I'm not sure, but I figured I'd mention it. 

Thoughts anyone?

---

### Post by unutbu on 2008-08-13
I can confirm that the CONFIG lines are kernel configuration options.
You can check your current kernel configuration options -- they are in the file /boot/config-$(uname -r).

On my Gutsy system, they were compiled as modules:
```

% grep CONFIG_SATA_NV= /boot/config-$(uname -r)
CONFIG_SATA_NV=m
% grep CONFIG_SCSI= /boot/config-$(uname -r)
CONFIG_SCSI=m
% grep CONFIG_BLK_DEV_SD= /boot/config-$(uname -r)
CONFIG_BLK_DEV_SD=m
```

---

### Post by kernalsanders123 on 2008-08-13
I get the same for my Gutsy install and my Hardy LiveCD. Perhaps if I could recompile a Hardy kernel, enabling CONFIG_SATA_NV and CONFIG_SCSI? My only doubt there would be, as my previous posts show, the sata_nv driver picks up my SATA CD drives fine, but it's worth a try I figure, thoughts?

*just to confirm, putting an =y at the end enables that particular configuration, while =n disables it, and =m compiles it as a module? That's what I seem to be getting from looking around. If so, I'd imagine recompiling with =y at the end of CONFIG_SATA_NV and CONFIG _SCSI wouldn't do much good, since they already have =m at the end, hence being compiled as modules. Of course, if my whole logic behind my theory is flawed, any corrections would be welcome.

---

### Post by unutbu on 2008-08-14
Yes, =y means the code is compiled into the kernel, =m means the code is compiled as a module which the kernel can load or unload as needed. 

Here are some guides on compiling kernels:
tseliot kernel compilation [http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)
KernelCheck [http://ubuntuforums.org/showthread.php?t=618563&highlight=KernelCheck](http://ubuntuforums.org/showthread.php?t=618563&highlight=KernelCheck) 
Master Kernel Thread [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)
How To Compile A Kernel [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by insane_mick on 2008-08-14
I've also been having a problem with SATA hard drives not being detected on 8.04.  I just bought two new systems and they both are having the same issue.  The First system is a Shuttle KPC K45 with an Intel 945GC chipset and the other is a ASUS M3A78-EM with an AMD 780G chipset.  

I was able to successfully install 7.10 on the Shuttle.  However, it will not allow X to start.  I also tried upgrading it to 8.04, but it freezes during the upgrade.

I checked the messages and I am getting the following error:
Aug 14 15:45:49 ubuntu kernel: [   44.603251] ata2: SATA link down (SStatus 0 SControl 300)
Aug 14 15:45:49 ubuntu kernel: [   45.078294] ata: SEMB device ignored

I have tried the following kernel arguments, but none of them have worked:
all-generic-ide
pci=nomsi
generic.all-generic-ide=1

I guess something has changed with the way SATA hard drives are handled.  Every review of the KPC said that it was a "breeze" to install, but I working on this for nearly a month.

They both work fine with XP, which is a real disappointment.

---

### Post by BlockBomb on 2008-08-20
I too have this problem, I've just finished building my computer and I can't seem to get the 8.04.1 liveCD to recognize the hard drive to partition it either.  

Intel Core 2 Duo E8400
Nvidia Geforce 8800GT
biostar t43
Western Digital 400GiB S-ATA


EDIT: I did what cariboo907 said and changed the sata setting to AHCI in the bios. it seemed to work,

---

### Post by kernalsanders123 on 2008-08-20
Well, that certainly makes things more interesting. Up until now it seemd I only found Nvidia chipsets with this problem. I checked my  bios, but I'm pretty sure my chipset doesn't support SATA. The only thing I can really do as far as SATA is concerned on my mobo is to turn the on-chip controller on and off, which doesn't help in either setting.

---

### Post by insane_mick on 2008-08-20
The really odd thing is that the Shuttle KPC was originally supposed to ship with Ubuntu.  So obviously someone has figured out how to deal with this issue.  I've seen places online selling the KPC with Ubuntu preinstalled.

Newegg sells a Linux installer USB stick for the KPC with Foresight linux for nearly $30.  So I tried rolling my own installer USB stick.  Foresight wouldn't detect the hard drive either.

I also tried installing Ubuntu on the WD SATA II hard drive in another system that already had Ubuntu 8.04 installed on an older SATA hard drive.  The other system also gave me the SEMB device ignored message.  So I suspect that there may be multiple issues going on.

](*,)

---

### Post by jmate24 on 2008-08-20
some hardware (i.e. video cards, motherboards, sound cards) don't like each other and they take up too many irqs and DMAs for the bios to handle and so when you try to install an OS and it does not recognize a piece of hardware because the OS is set to only recognize some to a few. And or that one piece of hardware (video card) will only work with only 1 or 2 irqs that the (SATA Bus) has hardwired. Hence trying to install a new copy of Vista (pre-SP1) on an brand new state of the art gaming pc from scratch. it also can have to do with a limited number drivers on the LiveCD. and the hardware (i.e. video cards, motherboards, sound cards) and on-board hardware all not willing to agree with each other. sometimes you just have to by a spare from a different chipset/manufacturer to see what works best. and return the other that does not work with your setup/OS.

---

### Post by insane_mick on 2008-08-23
I haven't made any progress yet, but I did finally find out what a SEMB device was.  Google wasn't very helpful the first few times I tried to look it up.

SATA Enclosure Management Bridge (SEMB) is some new SATA II extension for dealing with multiple drives in an external eSATA enclosure.  

So this tells me that the system does see the drive, it just isn't correctly identifying it in Linux.

---

### Post by kernalsanders123 on 2008-08-23
> **jmate24 said:**
> some hardware (i.e. video cards, motherboards, sound cards) don't like each other and they take up too many irqs and DMAs for the bios to handle and so when you try to install an OS and it does not recognize a piece of hardware because the OS is set to only recognize some to a few. And or that one piece of hardware (video card) will only work with only 1 or 2 irqs that the (SATA Bus) has hardwired. Hence trying to install a new copy of Vista (pre-SP1) on an brand new state of the art gaming pc from scratch. it also can have to do with a limited number drivers on the LiveCD. and the hardware (i.e. video cards, motherboards, sound cards) and on-board hardware all not willing to agree with each other. sometimes you just have to by a spare from a different chipset/manufacturer to see what works best. and return the other that does not work with your setup/OS.

I kind of see what you mean, but I never had any problems with previous versions of Ubuntu. I'll admit, I don't have much knowledge on irqs and DMAs, but I can confirm that my BIOS detects both of my hard drives on startup. As for the limited number of drivers on a LiveCD, the Hardy LiveCD uses libata and sata_nv, the same drivers that my current Gutsy install uses.

---

### Post by kernalsanders123 on 2008-08-27
Perhaps I might be jumping the gun here, but might it be worthwhile to submit a bug report to bugzilla.kernel.org? It seems to be a bigger problem than just tweaking a few things, and not just confined to this specific chipset.

---

### Post by kernalsanders123 on 2008-08-29
Another twist in this puzzling caper: I just bought an external HD, and running on eSATA, it was recognized without a hitch! So, I guess my theory of the whole sata_nv 3.5 driver being borked on my chipset is now null and void. However, both of my internal drives are Western Digital, and BlockBomb has also said that he has the same problem, with a Western Digital HD. Might that particular brand be the issue here?

---

### Post by insane_mick on 2008-08-29
My hard drives are also Western Digital WD3200AAJS 320GB.  I normally swear by WD so I don't have any other SATA drives to test out.

---

### Post by kernalsanders123 on 2008-08-30
OK, now I have no idea what to think. Looking at my device manager, my external hard drive also uses a Western Digital HD. So, my internals are listed as WD1600JS-62M, and my external is listed as WD5000AACS-0.

On this note, I am pretty much completely stumped. I've got sata_nv version 3.4 reading 2 types of WD hard drives, and version 3.5 reading only 1 version of WD hard drives.

On the plus side, apparently someone has filed a bug report for the same kind of problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/257790](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/257790)
Involves a WD SATA hard drive, and he gets SEMB device ignored message on startup.

No solutions from there as of yet.

What really stumps me is I can't really see any kind of pattern as to which kinds of drives are recognized and which kind aren't. Any possible insights, anyone?

---

### Post by kernalsanders123 on 2008-09-04
Another piece of the puzzle:

My Gutsy installation uses kernel version 2.6.22-15, which uses libata version 2.21, and sata_nv version 3.4. A Hardy LiveCD uses 2.6.24, libata 3.0, and sata_nv 3.5. I then downloaded and compiled kernel version 2.6.23-17, using libata 2.21, and sata_nv 3.5.

Gutsy detects all of my hard drives without issue. Hardy, with it's 2.6.24 kernel, only detects my external hard drive. Using Hardy with a custom compiled 2.6.23 kernel also detects all of my hard drives. So, apparently, sata_nv isn't necessarily the problem, since both 2.6.23 and 2.6.24 use sata_nv 3.5. However, 2.6.23 uses libata 2.21, while 2.6.24 uses libata 2.3.

Looking at wikipedia, libata is a "library" of ATA drivers and the like, including sata. So, my question is, how exactly does it interact with sata_nv? Is sata_nv a driver integrated into libata? And, if so, would this mean that my problem resides in the overall libata driver, and not sata_nv specifically?

---

### Post by insane_mick on 2008-09-10
I tried the new alpha release and it still does not detect the WD hard drive in the Shuttle system.  I tried it in my AMD 780g chipset system, but it won't boot completely.

It worked in 7.10, what happened??  Why isn't there a boot option to use the old drivers?  I don't care if its in IDE compatibility mode, I just want the thing to boot.

Has anyone else tried the new alpha release?  It's supposed to have the new kernel version.

---

### Post by fjgaude on 2008-09-11
I have had the Intrepid Alpha 5 work correctly in my main box, Gigabye MB DS4, 4GB of RAM, six sata hard drives, nvidia 7600 video, two DVD/CD RW pata drives. All okay. See my signature.

---

### Post by kernalsanders123 on 2008-09-11
Well, I think this seems to be a deep enough problem that a bug report to kernel.org is in order. However, I was about to file one, when I noticed a note saying: 

"NO BINARY MODULES or other tainted kernels. Do not file bugs here if you have any binary kernel modules loaded, reproduce without that module first.
NVIDIA users - THIS MEANS YOU!"

I know that sata_nv is used as a module, but the kernel I tried was the kernel downloaded from kernel.org. I'm not sure what a binary module is, so I'm not sure if sata_nv or libata count as binary modules, anyone happen to know if they are or not?

---

### Post by kernalsanders123 on 2008-09-17
Ok, figured out the binary modules thing, and also filed a bug report with the main kernel site: [http://bugzilla.kernel.org/show_bug.cgi?id=11579](http://bugzilla.kernel.org/show_bug.cgi?id=11579)

---

### Post by kernalsanders123 on 2008-09-19
Got it straightened out. After filing a bug report, I was sent a patch, which I compiled into a kernel, and lo and behold, it worked! Only hitch was I had to make sure the proper ALSA drivers were included, since apparently it didn't include them by default. So, if anyone here has the same problem, I'd recommend following the link I posted to my bug report, download the patch, and try it. It should tide one over until they (hopefully) fix it in the main kernel.

---

