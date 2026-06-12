---
title: "freeze: screensaver"
date: 2007-02-12
forum: General Help
---

### Post by eeried on 2007-02-12
Hello,

i've been trying to fix a computer which freezes from time to time -- then neither the keyboard nor the mouse work.

The motherboard is MSI k8MM-V. (built in sound and video).

removing the added video card seemed to have had a good effect (and reconfiguring Xorg of course).

However a screensaver caused the screen to freeze. Some screensaver seem to be ressource hogs but this computer has 512MB RAM which should be enough. Do you think this is a sign there's something wrong with the memory sticK?

What's going on? And why can't we choose which screensaver we want to disable. can't find this option that was there once in Dapper I'm sure. Which file can be edited?

:KS

---

### Post by an.echte.trilingue on 2007-02-12
What is the video card(s) in question?

---

### Post by eeried on 2007-02-12
The chipset is K8M800- VT8237R.
The card that had been added (and has been removed now) : Ati Radeon 9200 Pro with no extra drivers (just what Ubuntu installs when you install it.)

I've just realized Ubuntu boots on kernel 2.6.15-27-386 while I've upgraded to kernel 2.6.15-28.  As I installed Xubuntu  afterwards as dual-boot, Xubuntu grub menu.lst rules.  Howver i'm not sure this new kernel will solve any problems.

---

### Post by an.echte.trilingue on 2007-02-12
> **eeried said:**
> The chipset is K8M800- VT8237R.
The card that had been added (and has been removed now) : Ati Radeon 9200 Pro with no extra drivers (just what Ubuntu installs when you install it.)

ATI cards need a closed source driver called fglrx.  [Read this]("http://http://www.ubuntuforums.org/showthread.php?t=204910&highlight=ATI+radeon+howto").

As for your on board card, what is the output of lspci?

Take care
-mat

---

### Post by eeried on 2007-02-13
Hello an.echte.trilingue,

here's the output of lspci, with the ATI extra card removed:
```
0000:00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)
```


I think an ATI card needs this driver only if you want 3D which isn't needed at the moment.

I suspect there's something wrong with the memory. Memtest shows 6 errors in about 10 mns or less. It can be the memory stick or it can be the motherboard memory controller.

NB: after removing the extra video card I simply reconfigured Xorg completely with the plow option. Should I have installed a fresh Ubuntu?

---

### Post by an.echte.trilingue on 2007-02-14
While it very well could be a memory problem with the memtest issues you are having, I also have an S3 on board video card, and it also freezes like that under Ubuntu, but not under Debian.  I don't know exactly what the issue is, but I would suggest that if it does not go away you give Debian a shot.

As for the driver, no there are other things that the driver does for you.  I have a laptop with ATI graphics and it just blackscreens without the driver (even if I use Vesa).  It can't hurt.

Also, reconfiguring xorg should be all you have to do; no reinstall necessary.

Take care
-mat

---

### Post by eeried on 2007-02-14
I'd taken the addon video card out (the built in card is Via) and reconfigured Xorg, prior to having that screensaver freeze.

So I simply disabled all screensavers or blank screen, and things seem to be alright now.

Later this week I'll install a different memory stick, anf if things go well, I'll install the standalone card again, and install the extra drivers. one step at a time!

cheers

---

### Post by an.echte.trilingue on 2007-02-14
> **eeried said:**
>  (the built in card is Via) 

More specifically, it is an S3 Unichrome Pro, S3 Graphics being a joint venture between VIA Technologies and a company called SONICblue, which used to be called S3.

Unichrome cards are, in turn, integrated versions of the S3 Savage line built for VIA exclusively.

They aren't very good cards, but I find they crash less in Debian.

Take care
-mat

---

