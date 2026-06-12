---
title: "Slow io after upgrade to kernel 2.6.19..."
date: 2006-12-18
forum: General Help
---

### Post by Morientes on 2006-12-18
After I have switched to the 2.6.19 kernel I am having very slow disk access. F.ex when apt is reading the package database it takes a looong time compared to what it used to. I guess it is something wrong that I have included or something that I havent included when I compiled the kernel.

Anyone know what it might be?

---

### Post by Morientes on 2006-12-18
It seems DMA is turned off, but the usual hdparm command will not turn it on. It reports back with this:

sudo hdparm -d1 /dev/hdd1

/dev/hdd1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Invalid argument
 using_dma    =  0 (off)

So am I missing something in the kernel?

By the way I have a Asus P5N32-premium motherboard and a core 2 duo processor.

---

### Post by invalid on 2006-12-28
> **Morientes said:**
> It seems DMA is turned off, but the usual hdparm command will not turn it on. It reports back with this:

sudo hdparm -d1 /dev/hdd1

/dev/hdd1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Invalid argument
 using_dma    =  0 (off)

So am I missing something in the kernel?

By the way I have a Asus P5N32-premium motherboard and a core 2 duo processor.

In your case, you are specifying a partition instead of a drive. Try hdd instead of hdd1.

However, I am getting the following error on 2.6.20-2-generic.
```
beau@willow:~$ sudo hdparm /dev/hdc

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

beau@willow:~$ sudo hdparm -d1 /dev/hdc

/dev/hdc:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
```

I think there is a problem with one of the packages.. maybe initramfs? Does anyone have any ideas on where to start looking?

---

### Post by KyPeN on 2007-01-26
I am having the exact same issue.  I just upgraded to kernel 2.6.20-rc4 because it seems to be the only solution that allows nvidia drivers + ndiswrapper + broadcom bcm4311 drivers without IRQ conflicts.  

So I imported the old config file, recompiled, installed, and booted.  It locked up when it was trying to set up the "Waiting for Root File System...", or so I thought.  A little research later, I found out that it was searching for sda6, when it really needed hda6.  So I changed it and it takes forever to boot, runs slow, but works.  It is also worth noting that on the old kernel I was on sda6, hence the confusion.  I think it is also worth noting that, before I found out that I just needed to change the boot disk to hda6, I recompiled the kernel on suggestion from a friend with most of the essential stuff (ext3 support, sata support, pci-express) included in the kernel instead  of modules.  

Here is my output from the above commands.  

```

kypen@M1710 ~ $ uname -r
2.6.20-rc4-take2
kypen@M1710 ~ $ sudo hdparm /dev/hda

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 153356490, start = 0
kypen@M1710 ~ $ sudo hdparm -d1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
kypen@M1710 ~ $ 


```



Well, I've done some more homework.  I turns out that you have to compile chipset support into the kernel instead of a module.  Unfortunately, I can't seem to do it.  Honestly, I don't even know what I'm looking for.  My motherboard has an Intel Mobile 945gm/pm/gms/940gml and 945gt express PCI express chipset.  I have no idea what to compile into the kernel.  Can someone give me a hand?

---

### Post by KyPeN on 2007-01-26
I've run 3 different hdparm -Tt /dev/hda on my 3 different kernels:

Original (comes with ubuntu, don't remember version number)
Cache:  2754mbs
Read/Write: 44.18mbs

2.6.20-rc4 take 1 (without including what *may* be the proper chipset drivers in the kernel, but leaving them as modules)
Cache: 2723mbs
Read/Write: 1.67mbs

2.6.20-rc4 take 2 (including what *may* be the proper chipset drivers in kernel, not modules)
Cache: 2649mbs
Read/Write: 1.69mbs

As you can see, SOMETHING has gone totally wrong in this kernel upgrade.  I really think it has to do with SATA/IDE confusion in the kernel.  When I boot the 2.6.20-rc4, I have to specify it to be /dev/hda, not /dev/sda as with the stock ubuntu kernel.  

Please help!

---

