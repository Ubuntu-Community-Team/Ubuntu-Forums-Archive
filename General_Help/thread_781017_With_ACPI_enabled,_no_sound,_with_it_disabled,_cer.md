---
title: "With ACPI enabled, no sound, with it disabled, certain things don't work"
date: 2008-05-03
forum: General Help
---

### Post by Scooter7 on 2008-05-03
Hi,

With every Linux distribution I've tried, I always have to add 'acpi=off' to grub's menu.lst to get working sound.   The downside to this is that stuff doesn't work correctly afterwards.

I noticed with pleasure that upon upgrading to Hardy, the Power Manager applet actually reported when my laptop was running on battery, instead of saying it was running on A/C Power like it usually does, regardless of whether or not it really is.

I also noticed that I had no sound, due to the kernel upgrade, which means I had to modify menu.lst like I usually do.   After doing this and rebooting, I noticed that the Power Manager applet wasn't working correctly anymore.   This lead me to believe that it relies on ACPI to work.

Is there a way to get my sound working without disabling ACPI, or something?   Because although I don't necessarily need the Power Manager working right, it certainly is annoying, and there might be other issues which will be fixed if I can get things working with ACPI on.

---

### Post by articpenguin on 2008-05-03
post your hardware

> lspci

---

### Post by Scooter7 on 2008-05-03
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
0a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
0a:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

There's the output.

---

### Post by happyhamster on 2008-05-04
- Instead of disabling acpi completely, try disabling only parts of it. Instead of "acpi=off":

acpi=noirq

- or perhaps

pci=noacpi

---

### Post by Scooter7 on 2008-05-04
Neither of those options fixed the Power Applet problem, and both disabled my sound.   What is acpi for, anyway, and what is it?

---

### Post by Lizard787 on 2008-05-04
I'm having the same problems as you with every hardware part you listed exactly the same. You wouldn't happen to have a Toshiba laptop would it be a P105 . If so I think it is a DSDT problem. If you are using a toshiba laptop and the right model number you can find a fixed one at [http://www.linlap.com/wiki/Toshiba+Satellite+P105](http://www.linlap.com/wiki/Toshiba+Satellite+P105)
But becareful. I haven't tried that though. Anyway how is it you turn off acpi I know on livecd its like f6 then you say acpi=off
Ive been messing around with the /boot/grub/menu.lst
Don't you put it in the # kopt=root=UUID=b6947baf-ad16-4704-aeb9-ab225c7d84df ro apci=off like that but acpi is still on?
Here is how-to on inserting dsdt into kernel.
How to Build a custom DSDT into the kernel
------------------------------------------
Get original DSDT:
# cp /proc/acpi/dsdt DSDT
or
# acpidump > acpidump.out
$ acpixtract DSDT acpidump > DSDT

Disassemble it
$ iasl -d DSDT
Make your changes:
$ vi DSDT.dsl
Build it:
$ iasl -tc DSDT.dsl
Put it where the kernel build can include it:
$ cp DSDT.hex $SRC/include/

Add this to the kernel .config:

CONFIG_STANDALONE=n
CONFIG_ACPI_CUSTOM_DSDT=y
CONFIG_ACPI_CUSTOM_DSDT_FILE="DSDT.hex"

Make the kernel and off you go!
You should see in dmesg:
Table [DSDT] replaced by host OS

Note that with
CONFIG_ACPI_DEBUG=y
then ASL stores to the special object "Debug" will
come out in the dmesg.  eg

Store("hello world!", Debug)
Store(Local0, Debug)

[ACPI Debug]  String: [0x0C] "hello world!"
[ACPI Debug]  Integer: 0x00000042

As of linux-2.6.23, "acpi_no_auto_ssdt" if available
to prevent Linux from automatically loading all
the SSDTs listed in the RSDT/XSDT.  So with this option,
the SSDTs can be included in the DSDT override
to effectively create a DSDT+SSDT override.

Found off [http://kernel.org/pub/linux/kernel/people/lenb/acpi/patches/README.ACPI](http://kernel.org/pub/linux/kernel/people/lenb/acpi/patches/README.ACPI)

---

### Post by Scooter7 on 2008-05-04
I do have a Toshiba laptop, but it's a Toshiba Satellite Pro P100.   Close enough though, but I dunno about modifying my kernel, any side effects?

---

### Post by Lizard787 on 2008-05-04
Well if you did before it boots up where you have 3 seconds you could click esc. And one of the modes should be recovery mode so you should still be ok . I would think but I would back-up data just incase. But I believe kernel and acpi are two different things? I think this: [http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems](http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems)
is more what you're looking for?
However with ACPI you could kill your'e computer because it in some computers controls fans, thermal control, etc. So I would be very careful to make sure all fans are running and keeping things cool!

---

### Post by Scooter7 on 2008-05-04
I'm pretty sure everything works fine, except for hibernating, etc. (which I think is separate, not really worried about that) and the Power Applet.   I'll take a look at that link, though, thanks.

---

