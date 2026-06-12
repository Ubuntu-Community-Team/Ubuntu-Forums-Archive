---
title: "enable DMA in Lucid"
date: 2013-03-31
forum: General Help
---

### Post by Omo on 2013-03-31
so Brasero takes a bit less than an hour to burn a DVD, and I start to search for ideas, and I read about opening Terminal and typing **dmesg | grep ata** - so I do that and I get the results posted below. So, I'm looking to enable DMA. I didn't see anything specific to Lucid, so I thought I should ask about it here.

I should note that I get a few lines appearing during boot that informs me that ALi chipset isn't supported. Mainboard is an Asus socket A, with 2 GB of DDR RAM

[    0.000000]  BIOS-e820: 000000007ffd0000 - 000000007ffdf000 (ACPI data)
[    0.000000]  modified: 000000007ffd0000 - 000000007ffdf000 (ACPI data)
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000] Memory: 2052120k/2096960k available (4702k kernel code, 43460k reserved, 2124k data, 664k init, 1187656k highmem)
[    0.000000]       .data : 0xc0597bd7 - 0xc07aadc8   (2124 kB)
[    0.108406] libata version 3.00 loaded.
[    0.690148] pata_acpi 0000:00:0e.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.690199] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    1.309687] Write protecting the kernel read-only data: 1848k
[    1.576464] pata_ali 0000:00:0e.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.585580] scsi0 : pata_ali
[    1.594487] scsi1 : pata_ali
[    1.596702] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.596707] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.936434] ata1.00: ATA-6: ST3100011A, 3.02, max UDMA/100
[    1.936440] ata1.00: 195371568 sectors, multi 16: LBA48 
[    1.936480] ata1.01: ATAPI: PIONEER DVD-RW  DVR-115D, 1.06, max UDMA/66
[    1.936508] ata1.01: WARNING: ATAPI DMA disabled for reliability issues.  It can be enabled
[    1.936511] ata1.01: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    1.952334] ata1.00: configured for UDMA/100
[    1.968164] ata1.01: configured for UDMA/66
[    2.177814] ata2.00: ATA-7: Maxtor 6L200R0, BAJ41G20, max UDMA/133
[    2.177819] ata2.00: 398297088 sectors, multi 16: LBA48 
[    2.179401] ata2.01: ATA-7: Maxtor 6L200P0, BAJ41G20, max UDMA/133
[    2.179405] ata2.01: 398297088 sectors, multi 0: LBA48 
[    2.193702] ata2.00: configured for UDMA/133
[    2.209709] ata2.01: configured for UDMA/133
[    3.693720] EXT3-fs: mounted filesystem with ordered data mode.

---

### Post by dcstar on 2013-03-31
```
man hdparm
```

---

### Post by Omo on 2013-03-31
That appears to open a manual in Terminal, although I have to hit Enter to see each line. I did want to check in before going anywhere that Warning Flags are connected with, and the Community page on DMA did warn against incorrect use of HDPARM

I'll keep at the Enter key until the whole thing is displayed, make a copy of it, and read it over.


Well, copying and pasting the manual will take awhile, since I can't highlight the entire text. I thought I should meanwhile mention that I read [this page]("http://ubuntuforums.org/showthread.php?t=1558657&highlight=lucid+slow+burning") and could find the three locations mentioned in the procedure, but it gets beyond my experience when the first step looks to have me create a new file (my guess would be a plain text file, but it's just a guess) ~ Most of what I've done before in this vein would be to add a line or two to an existing text file, or placing a '#' before a line that is being taken out of circulation, while following a page of detailed instructions.

---

### Post by Omo on 2013-04-01
One of my problems here is that the [DMA page]("https://help.ubuntu.com/community/DMA") and the [hdparm page]("http://ubuntuforums.org/showthread.php?t=16360") don't happen to contain suggested commands for me to run, that worked when I copied them verbatim. Since one page makes reference to "/dev/hda" and another to "/dev/hdc", I tried both hda and hdc, and no joy. Device Manager didn't show hda or hdc or hd-anything. My hdparm.conf file contains a reference to hda, but it's preceded by # symbols

Anyway,  a second examination of Device Manager shows me that my DVD burner is identified by "/dev/sr0" ~ that makes all the difference. But that runs into another roadblock when I try a simple command to enable DMA

/dev/sr0:

 Model=PIONEER, FwRev=1.06, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=13395, BuffSize=64kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: unknown:  ATA/ATAPI-2,3,4,5,6,7

 * signifies the current active mode


 hdparm -d1 /dev/sr0

/dev/sr0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

At this point, I'm kind of dead in the water, and I'm wondering about that 3-step solution that traces back to [here]("https://bugs.launchpad.net/ubuntu/+bug/292142/comments/12") ~ even though the steps were applied in Intrepid and not Lucid, the near-matching mainboard (Asus with VIA chipset) makes it look worth trying.

BUT - I still don't know for absolutely certain whether step 1 has me creating a new text file by the name of "options" or whether it has a more complex name, like options-dot-something

I'm probably over-analyzing this, but I was hoping to get this right on the first try.

---

### Post by dcstar on 2013-04-02
If you need to set things then you must use sudo:

```
sudo hdparm /dev/whatever.....
```

---

### Post by CraigPid on 2013-04-02
I once had a problem where a hard drive was only working in PIO mode.It was taking forever to burn a disc with files that were on that HD.I had been doing some repairs in the pc & when I put the ide cable back on that HD I tried to put it backwards & pushed in one of the pins.That was the pin that carried the DMA data.I unscrewd the logic board and pushed the pin back into place and it worked.
Anyway I'm saying that you're on the wrong track if you think it's a software issue.Most definitely hardware.If that disc was capable of DMA any operating system from this century would use it.
Craig

---

### Post by Omo on 2013-04-02
Thank you for replying. I did use sudo prior to the terminal commands, but I didn't copy that part of the dialog. 

I should first ask about "Inappropriate ioctl for device" when I try to enable DMA, using the hdparm -d1 command. I kind of took it to mean nothing good, or at least nothing easily solved.

I'm running a lot of old hardware, from a pile of mainboards obtained long ago to experiment with dual-booting Linux and Windows 9x - many of them are socket A boards, with VIA chipsets. If it happens that those chipsets are unsupported by Linux now, then I'll just have to relegate them to limited-use backup machines.

If I can find my 512 MB DDR memory, I can swap out with the 1 GB sticks in use right now, (since the 9x OS won't boot up with the larger sticks in place), and try the DVD burning in Windows. That will tell me if I have a cable issue.


Another burning problem I was experiencing with Brasero, was that the mouse function was very flakey, with the cursor bouncing all over the screen during the burn. The reason I mention it now, is that the flakiness has now disappeared. I went ahead and gave the 3-step 'fix' (referred to earlier) a try. It did not get DMA enabled. I could not enable it manually. But it raised my burning speed a trifle (from 1.7x to 2.5x) and the mouse works as usual, now.

---

