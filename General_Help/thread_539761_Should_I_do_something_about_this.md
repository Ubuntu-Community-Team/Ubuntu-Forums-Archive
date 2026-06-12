---
title: "Should I do something about this?"
date: 2007-08-31
forum: General Help
---

### Post by eph1973 on 2007-08-31
Here is an excerpt from dmesg:

[   59.089143] Checking aperture...
[   59.089147] CPU 0: aperture @ 1110000000 size 32 MB
[   59.089148] Aperture too small (32 MB)
[   59.125838] No AGP bridge found
[   59.143029] Memory: 1019960k/1047488k available (2217k kernel code, 27140k reserved, 1162k data, 304k init)
[   59.219211] Calibrating delay using timer specific routine.. 3992.49 BogoMIPS (lpj=7984996)
[   59.219278] Security Framework v1.0.0 initialized
[   59.219286] SELinux:  Disabled at boot.
[   59.219312] Mount-cache hash table entries: 256
[   59.219499] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   59.219501] CPU: L2 Cache: 512K (64 bytes/line)
[   59.219504] CPU 0/0 -> Node 0
[   59.219528] SMP alternatives: switching to UP code
[   59.219901] Freeing SMP alternatives: 28k freed
[   59.220022] Early unpacking initramfs... done
[   59.526084] ACPI: Core revision 20060707
[   59.526333] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   60.199813] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   60.239863] Using local APIC timer interrupts.
[   60.289963] result 12464266
[   60.289964] Detected 12.464 MHz APIC timer.
[   60.290303] Brought up 1 CPUs
[   60.290345] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[   60.290347] time.c: Detected 1994.280 MHz processor.
[   60.290670] Time: 11:52:18  Date: 07/31/107
[   60.290711] NET: Registered protocol family 16
[   60.290801] ACPI: bus type pci registered
[   60.290808] PCI: Using configuration type 1
[   60.292976] ACPI: Interpreter enabled
[   60.292979] ACPI: Using IOAPIC for interrupt routing
[   60.293461] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   60.293466] PCI: Probing PCI hardware (bus 00)
[   60.294773] Boot video device is 0000:01:05.0
[   60.320462] PCI: Transparent bridge - 0000:00:14.4
[   60.320535] PCI: Bus #04 (-#07) is hidden behind transparent bridge #03 (-#04) (try 'pci=assign-busses')
[   60.320538] Please report the result to linux-kernel to fix this permanently

That last line there about reporting the result to linux-kernel to fix this permanently:  how would I go about doing that, and should I even worry about it.  I have not had any problems that I could see really, just shot that up to see what I could see, and saw that line there.  I am trying to make some sort of contribution to the community, and I figured if there was some sort of unreported bug, I should do something about it.

And if that's just a normal entry in dmesg, let me know that, too.

Thanks.

Running this on an HP pavilion zv6000 laptop with 1GB RAM, amd64 3200 processor.

---

### Post by 5-HT on 2007-08-31
You could report it to the upstream kernel devs from kernel.org via their bugzilla or the lkml.org mailing list. However, they will not even take a look at it until you compile a vanilla kernel and reproduce it there. Unless you want to do so (would be worthwile, but kernel devs won't look at your problem running the Ubuntu kernel because it's so heavily patched), best bet is to file a bug on launchpad for the Ubuntu kernel devs to take a look.
cheers,

---

### Post by PaulFr on 2007-08-31
Is your PCMCIA working ? One report indicates that this may have an effect on your PCMCIA.

**[http://www.linux.com/base/ldp/howto/BootPrompt-HOWTO-4.html](http://www.linux.com/base/ldp/howto/BootPrompt-HOWTO-4.html)** indicates that by setting this argument (pci=assign-busses), the kernel will assign bus numbers itself ignoring bus numbers assigned by the firmware. That should not hurt, but may help.

I would suggest you add the pci=assign-busses to your kernel line in /boot/grub/menu.lst and look for any differences in behavior (see **[https://help.ubuntu.com/community/GrubHowto#head-28c697721b2f5d2352e43074a55f4621c415293d](https://help.ubuntu.com/community/GrubHowto#head-28c697721b2f5d2352e43074a55f4621c415293d)** for where to add this, use **gksudo gedit** or similar). Hope this helps.

---

### Post by eph1973 on 2007-08-31
Yeah, so doing that noapic thing was bad.  It caused my laptop to hang up during the boot process, fortunately I was able to fix it by booting through the live CD.  I think I'll just live with it, as I went onto launchpad and it seems they are at least aware that it happens, and are likely to address it with a later update.  As of now they don't seem too terribly concerned about it, since it really hasn't effected me too much as of yet.  Thanks for the tips and help.

---

### Post by PaulFr on 2007-09-01
Sorry to hear that, and good that you could fix it.

I just noticed in the 2.6.22.6 commit list (**[http://article.gmane.org/gmane.linux.kernel/575750](http://article.gmane.org/gmane.linux.kernel/575750)**) the following checkin:
> Bernhard Kaindl (1):
      PCI: lets kill the 'PCI hidden behind bridge' message

So maybe when Ubuntu gets to 2.6.22.x this message will disappear.

---

### Post by tgalati4 on 2007-09-01
Try turning off "Plug and Play" OS in the BIOS.  This may help with the hardware detection.  Plug and Play is for Windows and Linux prefers to make its own decisions about hardware assignment.

---

### Post by eph1973 on 2007-09-01
> **PaulFr said:**
> So maybe when Ubuntu gets to 2.6.22.x this message will disappear.

That's what it looked like to me on launchpad, that they were going to have all that sorted out by 2.6.22.x.

---

