---
title: "slow usb drive?"
date: 2007-02-09
forum: General Help
---

### Post by cleentrax on 2007-02-09
[B]/// : : SOLVED! : : \\\
[/B]

I had two problems: #1, my motherboard (ECS NTU400 A with nforce2 chipset) apparently doesn't do usb at 480mbps in Linux (though it does in WinXP). The other problem is that my USB scanner was slowing down my PCI card to USB 1.1. Once I unplugged the scanner, and plugged my drives into the PCI card, I was able to get 480mbps.


I have a usb external drive (fat32) reporting as usb2.0, 12Mbps. That appears to be the speed of USB1.1. 2.0 should be 480Mbps, shouldn't it?

It's an ECS nforce2 motherboard.

---

### Post by Cstrikedish on 2007-02-09
Your motherboard supports usb 2.0 or not. Maybe you have to update the motherboard. Otherwise the problem happened on the usb external drive. It is a real usb1.1.

---

### Post by cleentrax on 2007-02-09
It's a standard 180gb ATA drive in a USB2.0 case. Perhaps it's a motherboard problem. It's definitely supposed to be 2.0.

---

### Post by cleentrax on 2007-02-09
Well, I've updated the motherboard bios, no improvement. I've also tried running the USB drives off of an old USB2.0 PCI card I had laying around.

Unfortunately, they're both still running at 12mbps. Not much fun when I'm trying to stream video and audio, and back up gigabytes of data.

Anyone have any thoughts? Please?

---

