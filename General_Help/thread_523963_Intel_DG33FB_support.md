---
title: "Intel DG33FB support"
date: 2007-08-12
forum: General Help
---

### Post by tnseditor on 2007-08-12
Hello,

I am thinking about getting a new Intel motherboard, DG33FB, for my brother.  Does Ubuntu 7.04 or 7.10 (beta) support it?  Here is a link: [http://www.intel.com/cd/channel/reseller/asmo-na/eng/products/desktop/bdb/dg33fb/feature/index.htm](http://www.intel.com/cd/channel/reseller/asmo-na/eng/products/desktop/bdb/dg33fb/feature/index.htm)

---

### Post by PacketCollision on 2007-08-14
I just bought this board today, and while the SATA, ATA, USB and onboard video (VESA driver) all work out of the box on Ubuntu 7.04  X86_64 Server, the network adapter is not recognized, nor is the sound.  I haven't found any drivers in an hour or so of googling, but Intel tends to be pretty Linux-friendly, so I'm hoping drivers will show up eventually.  Simply popping a network card in the case has turned this into a perfectly good machine for my needs.

lspci output
```

00:00.0 Host bridge: Intel Corporation Unknown device 29c0 (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Unknown device 29c2 (rev 02)
00:03.0 Communication controller: Intel Corporation Unknown device 29c4 (rev 02)
00:19.0 Ethernet controller: Intel Corporation Unknown device 294c (rev 02)
00:1a.0 USB Controller: Intel Corporation Unknown device 2937 (rev 02)
00:1a.1 USB Controller: Intel Corporation Unknown device 2938 (rev 02)
00:1a.2 USB Controller: Intel Corporation Unknown device 2939 (rev 02)
00:1a.7 USB Controller: Intel Corporation Unknown device 293c (rev 02)
00:1b.0 Audio device: Intel Corporation Unknown device 293e (rev 02)
00:1c.0 PCI bridge: Intel Corporation Unknown device 2940 (rev 02)
00:1c.1 PCI bridge: Intel Corporation Unknown device 2942 (rev 02)
00:1c.2 PCI bridge: Intel Corporation Unknown device 2944 (rev 02)
00:1c.3 PCI bridge: Intel Corporation Unknown device 2946 (rev 02)
00:1c.4 PCI bridge: Intel Corporation Unknown device 2948 (rev 02)
00:1d.0 USB Controller: Intel Corporation Unknown device 2934 (rev 02)
00:1d.1 USB Controller: Intel Corporation Unknown device 2935 (rev 02)
00:1d.2 USB Controller: Intel Corporation Unknown device 2936 (rev 02)
00:1d.7 USB Controller: Intel Corporation Unknown device 293a (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation Unknown device 2912 (rev 02)
00:1f.2 SATA controller: Intel Corporation Unknown device 2922 (rev 02)
00:1f.3 SMBus: Intel Corporation Unknown device 2930 (rev 02)
02:00.0 IDE interface: Marvell Technology Group Ltd. Unknown device 6101 (rev b1)
06:01.0 Mass storage controller: Silicon Image, Inc. PCI0680 Ultra ATA-133 Host Controller (rev 02)
06:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
06:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

```

Note: "06:01.0 Mass storage controller: Silicon Image, Inc. PCI0680 Ultra ATA-133 Host Controller (rev 02)" is a PCI ATA controller, to allow my PATA JBOD to be used in a box with only one onboard PATA channel.
"06:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)" is a PCI Realtek 8169 Gigabit Ethernet card that I had lying around, I had some IRQ (I think) problems with it initially, but everything sorted itself out.  


Overall, at this time I would not suggest this board if you have other, better supported, options.  However, if you're using it primarily as a server, or don't mind having to add some cards to get full functionality, it seems very solid so far, and if support gets better, I would highly recommend it.

---

### Post by tnseditor on 2007-08-14
I have ordered two of them (one for me and one for my brother).  It's good to know that everything works but the sound and network.  Network cards are cheap (I have at least one lying around here) and we both have sound cards.  Thanks for the reply.  I will also see how it works with Gutsy.  I'll post back here when I find out if someone hasn't already by then.  The boards are supposed to be here on Thursday.

---

### Post by tnseditor on 2007-08-16
Everything came today much to my surprise.  Everything including the sound and network seems to work with Gutsy 7.10.

---

### Post by jesse0 on 2007-08-21
Hey TNS, I'm using Feisty on a very similar board and I can't get the sound card working. Which driver are you using?

Thanks!

Jesse.

---

### Post by PacketCollision on 2007-08-21
I too have found everything to be working in Gutsy (including intel accelerated X driver and compiz-fusion), although the distro is certainly still very *alpha*.

@jesse0: if you really want to try to get sound, etc. working, you're probably going to have to backport 2.6.22 from gutsy.  I tried to do it on my own (a bit of hubris there) and had no luck, but just now I found [this]("http://ubuntuforums.org/showthread.php?t=511974") thread, which claims to show how to do it.  I'll edit this comment when I try it out.

EDIT: I haven't changed my kernel, but with 2.6.20-16 sound is now working out of the box on a clean install of Feisty.  It appears to be using the snd_hda_intel module.  I did a netboot install and chose ubuntu-desktop.

---

