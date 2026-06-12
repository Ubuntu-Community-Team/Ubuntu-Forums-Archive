---
title: "Slow CD Ripping with Sound Juicer"
date: 2008-04-19
forum: General Help
---

### Post by chiefmanyrabbitguteat on 2008-04-19
When ripping CDs with Sound Juicer, I have noticed that the CD speed rarely goes over 5.0x.  This is regardless of what format I rip with (though I prefer ogg).  I have disabled Paranoia.  My processors aren't working very hard at all (Core2Duo 1.83 Ghz).  In Windows, a similar rip goes 4 times quicker.

Does anybody else have this problem?  How can I fix it.

---

### Post by grahams on 2008-04-19
Check to see if DMA is turn on for your device

hdparm -i /dev/scd0 (or whatever your device is)

n my system I get the following

hdparm -i /dev/scd0

/dev/scd0:

 Model=DW-224E                                 , FwRev=A.0H    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 *mdma2 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5

 * signifies the current active mode

If you don't see a DMA mode set, you can turn it on with hdparm -d /dev/scd0

---

### Post by chiefmanyrabbitguteat on 2008-04-21
I have UDMA turned on, but I cannot turn on DMA with that command.  It gives me the following error:

> /dev/cdrom:
 HDIO_GET_DMA failed: Inappropriate ioctl for device

I found some other threads, and I tweaked my /etc/hdparm.conf file, adding the following lines:

/dev/cdrom {
	dma = on		   
	interrupt_unmask = on
	io32_support = 1
	read_ahead_sect = 1024
}

I was ripping some pretty scratched CDs, so I turned Paranoia up to 8 again, and averaged around 6-8x in the rip.  Some clean CDs I had went as high as 12x.  Still not as fast as Windows, but an improvement nonetheless.

---

