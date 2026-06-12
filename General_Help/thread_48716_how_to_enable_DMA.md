---
title: "how to enable DMA?"
date: 2005-07-13
forum: General Help
---

### Post by pacz on 2005-07-13
I've tried **sudo hdparm -d1 /dev/hdb**

which gives this:

/dev/hdb:
setting using_dma to 1 (on)
HDIO_SET_DMA failed: Operation not permitted
using_dma = 0 (off) 

I've tried putting via82cxxx in /etc/modules
**lsmod** gives this:
....
....
via82cxxx              12956  0
ide_core              118988  5 piix,ide_generic,ide_disk,ide_cd,via82cxxx
....
....

I've tried adding this:

/dev/hdb {
dma = on
}

into /etc/hdparm.conf



but I still can't enable DMA

And those are all the things I've seen on the Ubuntu forums. What do I do next?

---

### Post by manicka on 2005-07-13
[http://www.ubuntuforums.org/showthread.php?p=93238#post93238](http://www.ubuntuforums.org/showthread.php?p=93238#post93238)

---

### Post by pacz on 2005-07-13
hmm... didn't see that before.
Sounds kind of scary  :neutral: but I'm up for an adventure  :)

edit:
Nothing in that post has helped me.  I tried removing all ide- modules from /etc/modules but that didn't help at all.  When I put them back in, I reversed their order with respect to the via82cxxx module, putting the former at the top and the latter at the bottom.  That also made no difference.

So now what?

---

### Post by pacz on 2005-07-13
I realized that I should have used piix instead of via82cxxx, used it, no difference.

---

### Post by coolclassic on 2005-07-13
In the etc/modules try putting via82cxxx before ide-cd,ide-generic

in the /etc/modules 

via82cxxx
ide-cd
ide-generic

---

### Post by pacz on 2005-07-14
I've already tried that, but it didn't work.

However, I did a sudo **hdpram -i /dev/hdb** and it listed the pio, dma, and udma modes... and apparently I'm already configured to use UDMA2.  So perhaps the problem is elsewhere.  I don't know where to look, so I'm going to try installing Mplayer, reinstalling libdvdthings and whatnot.

---

### Post by pacz on 2005-07-15
I've tried reinstalling things.  No luck.
Did a **hdparm -c3 /dev/hdb** and that seems to have sped the transfer up by 1 meg/sec:
```

pacz@ubuntu:~$ sudo hdparm -tT /dev/hda
/dev/hda:
 Timing cached reads:   4292 MB in  2.00 seconds = 2144.18 MB/sec
 Timing buffered disk reads:   12 MB in  3.43 seconds =   3.50 MB/sec
```

That used to be about 2.6 MB/p instead of 3.5.

I have two conflicting reports concerning DMA and UDMA.  I hypothesize that although UDMA2 is selected for my drive, using_dma is not, and the latter is what matters.

```
pacz@ubuntu:~$ sudo hdparm /dev/hda

/dev/hda:
 IO_support   =  3 (32-bit w/sync)
 unmaskirq    =  1 (on)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

pacz@ubuntu:~$ sudo hdparm -i /dev/hda

/dev/hda:

 Model=ATAPI DVD DD 2X16X4X16, FwRev=G7H9, SerialNo=
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
```

I still get the error:

```
pacz@ubuntu:~$ sudo hdparm -d1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
```

no matter what DMA setting I try.  I'm beginning to think I won't escape this one without recompiling my kernel  :neutral: 

any more ideas?

---

### Post by pacz on 2005-07-15
For all the trouble I see with this problem, I can't believe I couldn't find more information more quickly.  I finally got it working and I'll be posting a howto about it.

---

### Post by go_bears on 2005-07-31
[QUOTE=pacz]For all the trouble I see with this problem, I can't believe I couldn't find more information more quickly.  I finally got it working and I'll be posting a howto about it.[/QUOTE]
 Have you had  a chance to work on that DMA howto?  I'm having the same problem you have.  Thanks.

---

