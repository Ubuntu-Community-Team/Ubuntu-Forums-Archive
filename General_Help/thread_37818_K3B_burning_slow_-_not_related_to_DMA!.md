---
title: "K3B burning slow - not related to DMA!"
date: 2005-05-28
forum: General Help
---

### Post by freshdaemon on 2005-05-28
Hi folks,

When burning DVDs, K3B averages between 0.8x and 1.2x. This is on an LG 16x burner with 8x Sony media that works at full speed under Nero on Windows. I have already played around with the hdparm settings, here is the part of the .conf that pertains to the burner:

> command_line {
	hdparm -X66 -c3 -d1 /dev/hdd
} 

This is the output of hdparm -i :

> /dev/hdd:

 Model=HL-DT-ST DVDRAM GSA-4163B, FwRev=A104, SerialNo=K2552I11324
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no
 Drive conforms to: device does not report version:

 * signifies the current active mode 

This is the output of a straight hdparm command:

> /dev/hdd:
 IO_support   =  3 (32-bit w/sync)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument 

Any ideas what else I can do?

---

### Post by DanP on 2005-05-29
As I recall, this is  a known problem with burning DVD's in Linux especially under K3B.

I have found that xcdroast is faster once you have gone the extra steps to allow it to
burn DVD's.  If you are interested in xcdroast be sure to read the instructions for how
to enable DVD burning-- it entails downloading an extra (seperate) program,
but it does burn DVD's faster when you are done.

HTH,
DanP

---

### Post by freshdaemon on 2005-05-29
xcdroast seems much better! I installed it and set it up for DVD-burning, and now the speed will hover somewhere between 6x and 9x, on average. It'll drop down to 1.2x or so when beginning or ending a particular track or file, but these results are identical to what Nero was giving me under Win32.

Thank you for your help!

---

### Post by DanP on 2005-05-30
Glad it's working out well for you.  Thanks for the reply letting us know how it worked out.

Best regards,

DanP

---

### Post by rizzyc on 2006-01-03
I installed this xcdroast program but i'm a newbee and dont know how to configure it.. it says no root configuration file found or not reachable the super user must start and configure it i dont konw how to do that :(

---

### Post by tombott on 2006-01-06
This may help

[http://www.esrf.fr/computing/cs/intro/burners.htm](http://www.esrf.fr/computing/cs/intro/burners.htm)

Launch X-CD-Roast by Applications - System Tools - Run as different user

In the run box type:

xcdroast

X-CD-Roast will now lauch, follow the guide listed above and you should be ok.

---

### Post by rizzyc on 2006-01-08
thanks for the help tombot but now im getting this error in the window
"No Cd-writer or cd-rom devices detected.
For Atapi/IdeE devices under Linux you have to enable SCSI-Emulation in the kernel in order to activate them.

I think i managed to add my dvd rom and cd rom but it looks like this is only for cd roms?

---

### Post by halitech on 2006-03-23
thank you tombott, I was wondering myself how to use xcdroast cause I was getting the same error and I've been having the same slow burning issues with k3b both using iso's and dvd video options. hope this helps out once I install ProDVD

---

