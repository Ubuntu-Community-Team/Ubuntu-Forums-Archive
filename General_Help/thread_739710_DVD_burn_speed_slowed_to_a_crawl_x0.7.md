---
title: "DVD burn speed slowed to a crawl x0.7"
date: 2008-03-30
forum: General Help
---

### Post by cinamax on 2008-03-30
Hello,

I'm having a problem in Ubuntu GUTSY (7.10). I have an IDE DVD-RW installed and it's using ide_cd drivers as per lsmod. My burn speed is at a pathetic x0.7 under k3b. However, my read speed is ultra fast.

I checked hdparm -i and see that udma 32 bit, etc. are turned on just as directed.

will chown root:cdrom /dev/dvdrw do the same trick for me as doing it under /dev/sg0 (for those who has ide_scsi)? 

Or should I look into changing my ide dvdrw to use scsi emulation instead ?

Please help, I can't burn any DVDs without waiting two hours. My reading speed is decent as DVD ISOs are created under 8 minutes or so.

---

### Post by cinamax on 2008-03-30
does anybody have a solution to this? I really hate going back to vista just to burn ISOs that I created in Ubuntu.

i got rid of k3b and installed GnomeBaker. it uses wodim instead of genisofs and it seems a little faster but not by much. It's taking 30 minutes to burn a 3.2 GB ISO.

Is this a IDE driver problem? config? app ? ...etc?  anybody know?

---

### Post by danwood76 on 2008-03-30
You could also try brasero.

What DVD drive do you have and also what motherboard/PC?

---

### Post by cinamax on 2008-03-30
> **danwood76 said:**
> You could also try brasero.

What DVD drive do you have and also what motherboard/PC?

I don't remember the brand myself. It does not show on the front face either so I'm guessing it was IOMagic. 

 Model=ATAPI DVD DD 2X16X4X16, FwRev=G7C9, SerialNo=B5C150C143504234SP
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no

 * signifies the current active mode

It's on AMD Athlon XP processor (2.2Ghz) --mobo its Gigabyte.



Still can't get it to burn as fast as in winxp... it seems something is wrong with the drivers because GnomeBaker and k3b all said burning @ 16.13x (but actual burn rates are 0.70x and 2x)


How do I fix it?

---

