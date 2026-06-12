---
title: "Something causing UI freezes, while mouse cursor still active"
date: 2015-08-10
forum: General Help
---

### Post by GXdmWQH on 2015-08-10
Recently attempted to bung Ubuntu 12.04 LTS on my desktop, with KDE. Switching between KDE / Unity / XFCE as I can't decide which I want to use (stability from Unity vs customisation of KDE vs general niceness of XFCE).

Not entirely sure where to look to try solve it, I'm having an issue where sometimes (possibly related to opening a new tab) everything just hangs, but I can' still access terminals, run top, and see what's happening (ctrl + alt + F1 etc works). The mouse cursor still moves but nothing responds to input. I imagine there is an easy way to "restart" the window manager (which is presumably what's going wrong here?) but not sure how to, if anyone knows this, firstly, it would be great to hear about.

The second part of this (after I've found a way to recover the system when it does freeze) is to try prevent the freezing. It seems to happen when I open a new tab and have a large download on the go (have been downloading DotA2 over steam and it's crashed twice when I've opened new tabs). Perhaps this is something like a HDD locking up after being "over used"? Maybe two operations are running simultaneously and there's a deadlock going on? Has anyone had this experience before? Does anyone know how I might go about debugging it? Would be useful to know of an application not dissimilar to Windows resmon (Resource Monitor) which would tell you what is writing to and/or reading from disk, and what file handles are open etc. That might aid in debugging.

The machine in question has been notoriously unstable on both Linux Mint and Ubuntu in the past, and I've never had it stable running any Linux distro... The specs (for anyone who might think it could be related to hardware support) are:

[LIST]
[*]AMD FX8350 "Black Edition" (4.2GHz octo-core) CPU
[*]990FX-UD3 Motherboard (Sporting the infamously unsupported RTL8111E network chip, for which drivers must be downloaded from RealTek and built/installed manually - annoyingly difficult on a machine which has **no network connection **from which to download them.
[*]EVGA GTX 770 Graphics card (This works fine OOB, haven't tried anything other than the standard drivers for it yet - haven't installed any, just whatever Ubuntu uses by default)
[*]24GB RAM (different brands / models / whatevers). Plenty for even the workiest of horses.
[*]3 spinny disks, and 3 SSDs (because why the hell not? They are Intel SSDs and WD Blue HDDs)
[/LIST]

Aside from that it's hooked up to 2 27" Samsung monitors (not that I imagine they can make any difference, but having said that a load of audio drivers and crap are installed for them which I don't use). There's usually the odd USB stick wedged in somewhere, but all USB ports appear to work (all are USB3, no USB2 etc).

Any suggestions on this would be welcome, I'm stumped and want to work it out.

---

