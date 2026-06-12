---
title: "Some big second jumps in dmesg"
date: 2008-05-31
forum: General Help
---

### Post by markg85 on 2008-05-31
Hey,

Ubuntu is a distributions that's also known for it's relatively fast boot compared to other linux based distributions. I just looked over dmesg and saw some strange second jumps. Some that might need some improvement for the next ubuntu to make it even faster (< 30 seconds goal?)

Oke here are my findings:
```

[    0.000000] Detected 1596.038 MHz processor.
[   13.513720] Console: colour dummy device 80x25

```
Oke the fist ton of messages are all starting with 0.000000... why is that?
Is that the kernel boot? if that's the case then the kernel boot takes ages! 13.5 seconds.

```

[   13.658214] Early unpacking initramfs... done
[   14.401551] ACPI: Core revision 20070126

```

```

[   14.962179] checking if image is initramfs... it is
[   16.428470] Freeing initrd memory: 7674k freed

```

Oke take a good look at those 2 pieces of code. First initramfs is extracted! Then (0.5 seconds later) it's checked if it is a initramfs file which 1.5 seconds. The extracting took half of that and besides if it's extracted than why recheck if the image is initramfs.. it's already extracted so not even needed anymore! This could mean a 1.5 seconds boot gain. (if i'm right ofcause) And why is the checking taking so long (if it's even needed)!!

```

[   16.437542] isapnp: Scanning for PnP cards...
[   16.792132] isapnp: No Plug & Play device found
[   16.847236] Real Time Clock Driver v1.12ac

```
0.4 seconds wasted to tell me that there is no PnP device.. This needs to be way faster! (for example a microsecond!)

```

[   17.144361] fb0: VESA VGA frame buffer device
[   18.458272] fuse init (API version 7.9)

```

Not sure what to think of this one.. vesa should be a easy driver.. does it have to take 1.3 seconds to load?

```

[   18.513229] ACPI: Thermal Zone [TZ01] (52 C)
[   19.324830] usbcore: registered new interface driver usbfs

```

What is that "ACPI Thermal Zone"? it takes about 0.8 seconds!

```

[   20.296425] ata1.00: configured for UDMA/133
[   20.617006] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T10N, PP02, max UDMA/33

```

I have no clue what this is here but somehow it doesn't look good.

```

[   21.343626] EXT3-fs: mounted filesystem with ordered data mode.
[   33.015067] input: PC Speaker as /devices/platform/pcspkr/input/input2

```

Oke this is one of the biggest time jumos that i've found. It looks like mounting my 70GB EXT3 partition (only 1) takes well over 10 seconds! 11.7 to be precise. What's going on here? mounting a partition isn't taking so long when i do it manually. Bring this down to a few miliseconds and ubuntu will boot 10 seconds faster!

```

[   36.206709] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   36.206717] iwl3945: Copyright(c) 2003-2007 Intel Corporation

```
nothing wrong here
```

[   36.206949] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   36.434833] sdhci: Secure Digital Host Controller Interface driver

```

But something is here! First it tells me it has a driver for me then it detected it.. seems like a useless check to me and saves 0.23 seconds if removed.

```

[   38.472985] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   38.646132] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17

```

Isn't NetworkManager (in gnome) doing this as well?

```

[   39.902946] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   41.311130] ip_tables: (C) 2000-2006 Netfilter Core Team

```

So the initialization of the device mapper took 1.4 seconds.. kinda long.

And that was my last message from dmesg.
All in all a 41 second boot does sound nice but faster is better.

Now this is what i would save if all the above things would have a max of 0.2 seconds.

2 Seconds instead of about (rough estimate): 17 seconds.
Total boot time then would be: 41 - 17 = **24 seconds**
But that would be a best case scenario. i think about 30 up to 35 seconds is a safer bet. In those calulations i left out the first 13 seconds as possible speed improvements because i don't know what the time is of all those items except 0.000000 ;)

I hope i can get some responses on all the code parts above.
Imagine how fast it would boot when all the upstart stuff is done. (30 to 35 now when this got improved and probably 20 up to 25 with upstart)

---

### Post by markg85 on 2008-06-01
.. bump
it would be nice to see a opinion of someone else on my findings..

---

### Post by msrinath80 on 2008-06-01
So many are having problems just getting their hardware to work and your top concern is shaving 0.4 seconds here and 0.1 seconds elsewhere during boot? I'm sure there are those of us who would happily settle for a reasonably slow boot sequence as long as all our hardware is properly supported.

---

### Post by markg85 on 2008-06-01
> **msrinath80 said:**
> So many are having problems just getting their hardware to work and your top concern is shaving 0.4 seconds here and 0.1 seconds elsewhere during boot? I'm sure there are those of us who would happily settle for a reasonably slow boot sequence as long as all our hardware is properly supported.

my primary concern isn't the 0.4 seconds but the bigger ones like the 10+ seconds for mounting 1 ext3 partition

Also boot and driver concerns are 2 completely different subjects.

---

### Post by BlueSkyNIS on 2008-06-01
> ```
[   21.343626] EXT3-fs: mounted filesystem with ordered data mode.
[   33.015067] input: PC Speaker as /devices/platform/pcspkr/input/input2

```

Oke this is one of the biggest time jumos that i've found. It looks like mounting my 70GB EXT3 partition (only 1) takes well over 10 seconds! 11.7 to be precise. What's going on here? mounting a partition isn't taking so long when i do it manually. Bring this down to a few miliseconds and ubuntu will boot 10 seconds faster!


At 21.343626 seconds your EXT3-fs is already mounted. dmesg didn't say when the mount start, so we can't tell how much it took. 

But I must say that dmesg timings are rather confusing :confused:

---

### Post by markg85 on 2008-06-04
Any ubuntu developer (or someone that knows what he/she is actually happening) that can clear this up a bit?

---

