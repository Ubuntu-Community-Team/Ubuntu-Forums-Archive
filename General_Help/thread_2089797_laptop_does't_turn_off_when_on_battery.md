---
title: "laptop does't turn off when on battery"
date: 2012-11-30
forum: General Help
---

### Post by claracc on 2012-11-30
Laptop hp compaq 6720s, ubuntu 12.04 dual boot with win vista, fully updated, gnome fallback desktop.

lspci command: 

> ```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```


When on ac supply laptop turns off normally from menu or from command line: i.e. sudo poweroff

But when on battery, I try to turn off the computer from menu and it remains forever in the splash screen (ubuntu logo and dots going from red to white forever), it doesn't turn off, neither if I try with command line: sudo poweroff. The only way is to hold pressed turn off button.

Is there any workaround?. Would I fill a bug?

Thanks in advance

---

### Post by Impavidus on 2012-11-30
I've got no idea what could be your problem, but switching your machine of using the power button could damage your system (as you probably know). It's best to first try Alt+SysRq+(r, e, i, s, u, o). This should savely shut down your computer, even if the command line doesn't work. See [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key) for some details.

---

### Post by claracc on 2012-12-01
> **Impavidus said:**
> I've got no idea what could be your problem, but switching your machine of using the power button could damage your system (as you probably know). It's best to first try Alt+SysRq+(r, e, i, s, u, o). This should savely shut down your computer, even if the command line doesn't work. See [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key) for some details.

Thanks but, once in the splash screen after trying to turn off the laptop, it doesn't respond to any key combination I press: no alt+sysrq+RESUIB or any other as ctrl+alt+del or trying to run into console.

I know it can be harmful to turn off laptop from button but it is the only way.

---

### Post by BlinkinCat on 2012-12-01
> **claracc said:**
> Thanks but, once in the splash screen after trying to turn off the laptop, it doesn't respond to any key combination I press: no alt+sysrq+RESUIB or any other as ctrl+alt+del or trying to run into console.

I know it can be harmful to turn off laptop from button but it is the only way.

Not sure, but the correct sequence is REISUB

Cheers,

---

