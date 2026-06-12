---
title: "I get colored lines instead of GUI???"
date: 2005-08-13
forum: General Help
---

### Post by DiZASTiX on 2005-08-13
Hello, I've recently got around to trying the Ubuntu LiveCD, I booted it up and went through the config process perfectly (detected and configured everything without any trouble). After it's done and it starts to boot Ubuntu Live, at the point where it should boot into X and show the GUI, it instead shows colored vertical lines which change after a while...

The following are the specs for my computer:

    * Motherboard: MSI K8N Neo4 Platinum
    * Processor: AMD Athlon 64 3000+ Winchester
    * Memory: 1gb (2×512) OCZ PC3200 Platinum Revision 2
    * Video Card: BFG 6600 GT OC PCIe

I am using the Ubuntu AMD64/EM64T Live CD version 5.04. Any ideas what the problem is and if there is any way around it?

---

### Post by thegeronimo on 2005-09-08
Hello,

I got the same problem

When loading the Live CD it goes perfect until the boot into X. The only view I get then is colored lines and blocks.

My specs:
* Motherboard: Asus A8n-sli Deluxe
* Processor: AMD Athlon 64 3200+ Winchester
* Video Card: XFX Nvidia 6600 GT PCIe

I've used the latest 32bit live CD, downloaded from Gnome with Gnome 2.12

But this problem has occured with other live CD's and Distro's (Fedora) 32bit and 64bit

---

### Post by rafakl on 2005-09-08
I dont know if this can help, but why dont you run the livecd with "live-expert" and play around with the configuration options of the x server????

When the livecd boots and you see the ubuntu screen, dont press enter, write "live-expert" and press enter.

---

### Post by thegeronimo on 2005-09-08
[QUOTE=rafakl]I dont know if this can help, but why dont you run the livecd with "live-expert" and play around with the configuration options of the x server????

When the livecd boots and you see the ubuntu screen, dont press enter, write "live-expert" and press enter.[/QUOTE]

Oké that's possible, but what are the options I have then. I'm no pro in this so I if it's gonna be code, I haven't find any info for that.

---

### Post by rafakl on 2005-09-09
Dont worry, its not code.

Many of the options have defaults, so you only need to press enter key if you dont understand something.

The good stuff comes when you start configuring the x server, try selecting a lower resolution, leaving blank the space when the system asks for your video card memory, selecting another driver for your card (try nv or vesa), etc.

---

