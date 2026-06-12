---
title: "Wrong Aspect Ratio after upgrading to 12.10"
date: 2012-10-21
forum: General Help
---

### Post by kwanylongy on 2012-10-21
Hi all,

I have just upgraded my Ubuntu OS from 12.04 to 12.10. Since the upgrade, my monitor has been displaying with the wrong aspect ratio. I tried to select the correct one through System Settings\Display, yet all the options available were unsuitable. Anyone knows how to fix this? 

Many thanks!

[IMG]https://dl.dropbox.com/u/57345394/Screenshot%20from%202012-10-21%2019%3A56%3A21.png[/IMG]

---

### Post by Wim Sturkenboom on 2012-10-21
I'm sure that somebody will be able to help if you tell us more about your hardware and the resolution that you need (or the make/model/specs of the monitor).

---

### Post by kwanylongy on 2012-10-21
wim,

thanks for your reply.

The resolution I need is 1440x900. I have a TOPCON figo-19w monitor. And for the graphics card, I have a ATI 4850, though I am not sure about the make of the card

---

### Post by Wim Sturkenboom on 2012-10-21
lspci (run in terminal) will be of help to find the exact card.

```

lspci |less

```
Scroll around and check for VGA.

I can't be of much more help.

---

### Post by kwanylongy on 2012-10-21
Wim,

Thanks for the help, here it is

carlos@asurada:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV770 [Radeon HD 4850]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI RV770 HDMI Audio [Radeon HD 4850/4870]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by Cheesemill on 2012-10-21
Have you installed the drivers for your graphics card?

Go to System Settings > Software Sources > Additional Drivers.

---

### Post by kwanylongy on 2012-10-21
It says no additional proprietary software installed (see pic below)

I would imagine that I would have had it installed when I began using Ubuntu in 11.04, does this imply that the upgrade uninstalled the driver?

[IMG]https://dl.dropbox.com/u/57345394/Screenshot%20from%202012-10-21%2021%3A45%3A28.png[/IMG]

---

### Post by Cheesemill on 2012-10-21
> **kwanylongy said:**
> It says no additional proprietary software installed (see pic below)

I would imagine that I would have had it installed when I began using Ubuntu in 11.04, does this imply that the upgrade uninstalled the driver?

I believe so.

ATI stopped supporting the 4xxx series of card with their closed-source linux driver this summer. Unfortunately this means that your are already using the only driver available for your card.

There is a way to change resolution of your screen using this legacy driver (I believe using the xrandr command or Xorg.conf) but as I've never used ATI graphics cards you'll have to wait for someone more knowledgeable to come along and tell you how.

---

### Post by kwanylongy on 2012-10-21
ok, thanks for the reply.

But my graphics card did work back in 12.04. Does that imply rolling back to 12.04 would work again?

---

### Post by Lula_F on 2012-10-22
Hi, same problem here with ATI x1200. Any help would be warmly welcomed.

On a side note, I experienced [pretty bad problems]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/556782") with this card before, but I managed to have a usable system at least. Now everything is very slow and I think it's somehow related to graphics performance.

---

