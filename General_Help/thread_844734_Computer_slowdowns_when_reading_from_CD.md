---
title: "Computer slowdowns when reading from CD"
date: 2008-06-29
forum: General Help
---

### Post by STVA on 2008-06-29
Hello everyone, I am running 8.04.  Whenever I am reading from a CD, whether it be in Wine, or installing a native linux program, or ripping an audio CD in Soundjuicer, my computer always slows down to a hault.  Everytime the program is done reading the CD, everything returns to normal.

What is causing this masstive slowdown?  How can I fix it?

Please don't blame this on my hardware, this is never an issue on Windows XP.

---

### Post by VMC on 2008-06-29
> **STVA said:**
> Hello everyone, I am running 8.04.  Whenever I am reading from a CD, whether it be in Wine, or installing a native linux program, or ripping an audio CD in Soundjuicer, my computer always slows down to a hault.  Everytime the program is done reading the CD, everything returns to normal.

What is causing this masstive slowdown?  How can I fix it?

Please don't blame this on my hardware, this is never an issue on Windows XP.

Open a Terminal and type 'top' then have you cd read some data, and when it slows down look at the Terminal and see how much CPU % is consumed.

---

### Post by STVA on 2008-06-30
Thanks for the reply.  Sound Juicer uses about 50% of the CPU, which seems like a lot.

What should I do?

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7074 tom       20   0 80132  25m  14m R 51.3  2.7   0:06.17 sound-juicer

---

### Post by rubicon on 2008-06-30
Chances are, your device doesn't use DMA. Check it with *hdparm -i*, here's what it shows on my system:
```

$ hdparm -i /dev/scd0

/dev/scd0:

 Model=Optiarc DVD RW AD-7170A                 , FwRev=1.02    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no

 * signifies the current active mode

```
See that active mode? UDMA4 is the fastest, it doesn't use CPU power for reading ([http://en.wikipedia.org/wiki/Direct_memory_access](http://en.wikipedia.org/wiki/Direct_memory_access)), if your cd-rom drive uses something like pio3, it is no wonder it consumes a lot of cpu time. More info: [http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance#Changing_device_settings](http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance#Changing_device_settings)

---

### Post by STVA on 2008-07-02
Here's what mine says:



tom@desktop:~$ hdparm -i /dev/scd0

/dev/scd0:

 Model=LITE-ON COMBO SOHC-4836K                , FwRev=SPJ2    , SerialNo=2006021400024970    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-5

 * signifies the current active mode

---

### Post by VMC on 2008-07-02
> Sound Juicer uses about 50% of the CPU, which seems like a lot
Is Sound Juicer using files off of the cd to play music or something?

---

### Post by STVA on 2008-07-02
> **VMC said:**
> Is Sound Juicer using files off of the cd to play music or something?

No, that's for rip only.

CD reading is slowing down my computer so much that playing audio CDs is causing some lag, which should not happen.

---

