---
title: "Failure to boot with 12.10 &amp; 12.04.1 - boots fine with 11.10"
date: 2012-11-06
forum: General Help
---

### Post by jmmL on 2012-11-06
I've been experiencing problems with the latest ubuntu stable releases. I've installed 12.10, 12.04.1 and 11.10 all from USB, and they all function fine in LiveUSB mode.

However, **after installatio**n, when attempting to boot either 12.10 or 12.04.1, I will get a kernel panic within the first few seconds of selecting ubuntu from grub. My caps lock light flashes, and the only option is to hold down the power button on my laptop to switch it off.

11.10 boots fine (I'm typing from it now), as does Windows Vista. The laptop is getting old, and I have bought a replacement, but as far as I know, there are no hardware faults beyond a battery that lasts only 5 minutes.

It's been 2+ years since I was following the dev releases of ubuntu, but I've forgotten much of what I learned.  Here's a lspci in case that helps:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8600M GS] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
06:00.0 SATA controller: JMicron Technology Corp. JMB360 AHCI Controller (rev 02)
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)

```It's a laptop from circa 2007, with an Intel T5450 dual core, with 8600M GS nVidia dedicated graphics.

Any and all help will be extremely appreciated! I'd love to upgrade up to precise/quantal whilst waiting for my new laptop to arrive.

---

### Post by jmmL on 2012-11-06
I've installed the latest security updates for 11.10. This bumped the kernel version from 3.0.0-12 to -26. I get the same error with -26 - that is, I cannot boot at all.

If it would help, I should be able to capture a picture of the output to the screen when the kernel panic happens, by booting into -26 recovery mode.

To clarify, I am using the amd64 version in all cases.

---

### Post by jmmL on 2012-11-07
Bump!

---

### Post by jmmL on 2012-11-08
Bump! This seems like a major regression to me.

---

### Post by jmmL on 2012-11-09
**Bump**

---

### Post by jmmL on 2012-11-10
Bump

---

### Post by jmmL on 2012-11-11
Is there a sub-forum where this question would be better asked?

---

### Post by Wim Sturkenboom on 2012-11-11
> **jmmL said:**
> Is there a sub-forum where this question would be better asked?

Not a subforum
[http://askubuntu.com/](http://askubuntu.com/)
[https://answers.launchpad.net/ubuntu](https://answers.launchpad.net/ubuntu)

---

### Post by jmmL on 2012-11-11
> **Wim Sturkenboom said:**
> Not a subforum
[http://askubuntu.com/](http://askubuntu.com/)
[https://answers.launchpad.net/ubuntu](https://answers.launchpad.net/ubuntu)

Thanks for those links. I actually found my answer at askubuntu, via this page: [http://dan-orth.com/wp/installing-ubuntu-12-04-on-asus-u46e-resolving-boot-issue/](http://dan-orth.com/wp/installing-ubuntu-12-04-on-asus-u46e-resolving-boot-issue/)

The important step is setting noapic in grub.

I'll mark this thread as solved once I upgrade to 12.10 and experience no more problems.

---

