---
title: "Fresh installation 8.04, slowliness, &quot;jumping&quot; audio and DMA problem"
date: 2008-06-10
forum: General Help
---

### Post by raozuzu on 2008-06-10
First of all, hi to everyone :)

I've installed the new new Ubuntu release, the installation was 100% successful.
But since the first start I noticed some problems.
The most relevant is tha the system is always slow: the boot process is slow, the login and GNOME too. The most strange thing is that even a simple application (like a window of nautilus!) cause this slowliness. Is not ended, in fact, for example, the animation of the cursor in first moments is slow and then it became really fast, too fast... an analog thing happens to the song (in a music player) in the timeline.
Oh well... another main issue is that the audio "jumps" for every signle thing i do and also if I do nothing, this is really strange! The same things happen for the videos.

I thought it was a problem of my video card, but I thinck is not this the problem. I installed the correct drivers both from the ubuntu dialog and both envyNG and nothing has changed.

After I thought that the DMA on my hard disk was disabled, so I tried to enable it with the following result:
typing "dmesg | grep DMA" I got this:
```
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[   37.479148] ata1: SATA max UDMA/100 mmio m512@0xfebffc00 tf 0xfebffc80 irq 16
[   37.479152] ata2: SATA max UDMA/100 mmio m512@0xfebffc00 tf 0xfebffcc0 irq 16
[   38.103517] ata3: SATA max UDMA/100 mmio m512@0xfebff800 tf 0xfebff880 irq 17
[   38.103521] ata4: SATA max UDMA/100 mmio m512@0xfebff800 tf 0xfebff8c0 irq 17
[   54.216781] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[   54.216784] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[   54.380335] ata5.00: ATA-6: ST3160021A, 8.01, max UDMA/100
[   54.396257] ata5.00: configured for UDMA/100
[   54.723567] ata6.00: ATAPI: MATSHITADVD-RAM SW-9586, B100, max UDMA/66
[   54.723748] ata6.01: ATA-7: Maxtor 6E040L0, NAR61590, max UDMA/133
[   54.723760] ata6.00: simplex DMA is claimed by other device, disabling DMA
[   54.723763] ata6.01: simplex DMA is claimed by other device, disabling DMA

```
that makes me thinks it is not enabled, expecially because of the two last lines.
So i type "sudo hdparm -d1 /dev/disk/by-id/ata-Maxtor_6E040L0_E1NS742E" to enable the DMA but I see this:
```
/dev/disk/by-id/ata-Maxtor_6E040L0_E1NS742E:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

```

I also tried to add these two options in GRUB (one at time obviously):
```
clocksource=hpet
clocksource=acpi_pm
```
But I don't think something has changed.

The last thing I noticed is that the process called "ata/0" sometimes during any operation takes a considerable amount of CPU usage (I saw it throught top").

What could be the solution? :confused:

I hope someone can help me and I apologize for my bad english :)

EDIT: my hardware specs are:
- CPU AMD64 3500+
- RAM 1.5GB
- Video Card nVIDIA GeForce 6600

---

### Post by raozuzu on 2008-06-10
Well... I also tried adding the "irqpoll" option in grub but nothing has changed

---

### Post by raozuzu on 2008-06-10
Umh... I made a test using glxgears and this is the result:
```
:~$ glxgears
10459 frames in 5.0 seconds = 2091.670 FPS
10967 frames in 5.0 seconds = 2182.020 FPS
10407 frames in 5.0 seconds = 2078.542 FPS
10584 frames in 5.0 seconds = 2116.715 FPS
XIO:  fatal IO error 22 (Invalid argument) on X server ":0.0"
      after 38 requests (38 known processed) with 0 events remaining.

```

Is it helpful for you? I'm not able to understand what error is giving to me

---

### Post by adamorjames on 2008-06-10
That error is because you closed the window.

---

### Post by raozuzu on 2008-06-10
> **adamorjames said:**
> That error is because you closed the window.

d'oh! :P
It'll be great if my other problems with ubuntu were a my error :lolflag:

---

### Post by raozuzu on 2008-06-10
I also tried the "lapic" boot option but nothing... I also reinstalled the "ubuntu's" nvidia drivers but nothing again... >:\

---

### Post by raozuzu on 2008-06-10
up :(

---

### Post by raozuzu on 2008-06-10
I think this could be called "one man topic" now... XD T_T

Well... In xorg.conf in "device" section I've added:
```
Option "UseEvents" "True"
```

that PARTIALLY solved my high CPU usage problem. In fact the CPU usage still encrease strangely when I run any applications (except for really simple apps like GNOME games).

Now I'll be really happy if someone could help me in some way :P

---

### Post by Tom Mann on 2008-06-10
Hi, is your installation up to date? There have been various problems similar to yours that went away with a kernel update for a lot of people - try that if you can.

Otherwise, you may need to go into your BIOS and enable/disable (whatever is the opposite) to the "Enable APIC" setting (if you have it)

---

### Post by raozuzu on 2008-06-11
Yes, my ubuntu is up to date (with kernel 2.6.24-19)

and nothing changed disabling ACPI in the bios.
The boot process always lasts more than 3-4 minutes and the CPU (or its fan) always seems a starting rocker :(

---

### Post by raozuzu on 2008-06-11
I've also tried with "acpi=off" and "noapic" boot options but nothing has changed...

I'll make a movie about this :popcorn:

---

### Post by raozuzu on 2008-06-11
up :cry:

---

### Post by raozuzu on 2008-06-11
Well... I read about the new x.x.25 kernel... shoul I try it?

---

### Post by raozuzu on 2008-06-11
> **raozuzu said:**
> Well... I read about the new x.x.25 kernel... shoul I try it?

Nothing... I've read this is useless :S

---

### Post by adamorjames on 2008-06-12
Have you asked people in the IRC channel #ubuntu on irc.freenode.net or irc.ubuntu.com? Also you may try the #linux channel. [http://www.mibbit.com/](http://www.mibbit.com/) 
Or if worst comes to worst a re-installation or a different Ubuntu version or a different distro.

---

