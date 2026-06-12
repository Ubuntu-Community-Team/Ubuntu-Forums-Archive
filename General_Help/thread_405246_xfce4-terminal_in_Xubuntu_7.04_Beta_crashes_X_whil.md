---
title: "xfce4-terminal in Xubuntu 7.04 Beta crashes X while using 'chips' driver"
date: 2007-04-09
forum: General Help
---

### Post by Slim Backwater on 2007-04-09
After completing a Xubuntu 7.04 beta install to an old Compaq Armada 1700, starting xfce4-terminal crashes X, and I'm prompted to login again.

I completed an apt-get update, upgrade and dist-upgrade (quite a few updates there) and it still continued to crash.

I changed xorg.conf from the 'chips' driver to 'vesa' and the crash went away.

With the 'chips' driver, Firefox works, the file manager works, even the usb network card. but no terminal.

My Xorg.0.log.old ends with:
```

Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) Open APM successful
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) Open APM successful
(II) Configured Mouse: ps2EnableDataReporting: succeeded

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]
2: /usr/bin/X(Xfree+0x21) [0x81a6171]
3: /usr/lib/xorg/modules//libxaa.so [0xb7a87eb6]
4: /usr/bin/X [0x815b8a4]
5: /usr/lib/xorg/modules/extensions//libextmod.so [0xb7c64c00]
6: /usr/bin/X [0x8137a4f]
7: /usr/bin/X(ChangeWindowAttributes+0xd35) [0x807b9a5]
8: /usr/bin/X(ProcChangeWindowAttributes+0xa0) [0x808c2e0]
9: /usr/bin/X [0x8142531]
10: /usr/bin/X(Dispatch+0x19f) [0x808c61f]
11: /usr/bin/X(main+0x495) [0x8074785]
12: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d83ebc]
13: /usr/bin/X(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal server error:
Caught signal 11.  Server aborting

```

Which doesn't mean a whole lot to me.

Here is lspci:
```

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:08.0 VGA compatible controller: Chips and Technologies F65555 HiQVPro (rev a8)
00:11.0 CardBus bridge: Texas Instruments PCI1220 (rev 02)
00:11.1 CardBus bridge: Texas Instruments PCI1220 (rev 02)

```

The laptop is pretty weak, a Pentium II @ 233 w/ 160 MB RAM and 4 GB HDD.

The only bug I found related to xfce4-terminal was [99170]("https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/99170/") but X isn't crashing in that case.

I don't know of any significant difference between the 'chips' and 'vesa' drivers, considering the age of the hardware, so I could probably live with the VESA driver, but I'll leave this note in case someond else is having similar trouble.

._.

---

### Post by DougieFresh4U on 2007-04-09
I filed a bug on that back in December or early January, but as I found out a couple of days ago, nothing done yet. I had to install gnome terminal and was using that on my Xubuntu machine

---

### Post by kid_a on 2007-04-20
i have the same problem, my terminal crashes and then xubuntu logs out, but now i have the stable version since yesterday (19/04/07), what's going on??

---

### Post by MethodOne on 2007-04-23
This also happens on an IBM Personal Computer 300PL with a 400 MHz Pentium III and an S3 Trio3D graphics chipset.  I am using the s3virge drivers.  After I switched from "vesa" to "s3virge", running xfce4-terminal logs me out.  That didn't happen with the vesa drivers, but I only get a resolution of 640x480 if I switch back.  I'll use xterm or gnome-terminal for now until this problem is resolved.

---

### Post by joylessdave on 2007-04-27
i have the same problem on a intel n440bx board with dual 400mhz pII and 512mb of ram

it has a cirrus logic gl5480 graphics chip 

running the cirrus driver

edit - after installing gnome-terminal and all the dependancies via synaptic xfce4-terminal has randomly started working

---

### Post by neophyrigian on 2007-04-30
The master entry for this issue is [Bug #91849]("https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/91849") in Launchpad with some duplicates; the bug is assigned to upstream, xfce Bugzilla, [Bug 3130]("http://bugzilla.xfce.org/show_bug.cgi?id=3130")

For the time being, installing gnome-terminal seems to be a smart move.

Personal comment: Neither assigning the bug to upstream nor using gnome-terminal proposal doesn't solve the problem for xubuntu front. This is the default terminal coming with xubuntu and if it isn't working for this reason or that, xubuntu should find a solution of their own including the option replacing it with some other tool.

---

