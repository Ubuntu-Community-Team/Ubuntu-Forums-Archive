---
title: "HELP!!!! Weird messages at startup!!!"
date: 2008-02-22
forum: General Help
---

### Post by Redrazor39 on 2008-02-22
Ok, right after the grub menu and selecting ubuntu, I see:

```
Starting up...
PCI: **Failed to allocate memory resource #6** 437531073981740371
```

It's something like that, I don't know what it says EXACTLY, but the part in bold I'm certain of.

Then my screen flashes green

Then ubuntu boots normally


How do I fix this so it succeeds in allocating this or w/e and make that green screen go away?

---

### Post by lifewithryan on 2008-02-22
Well, (at the risk of stating the obvious):

it appears that you have some PCI device that is having some issues.  Any chance you can run the following command after it boots and past it back here?

```

sudo lspci

```
*the sudo may not be necessary now that I think of it.

What that should do is spit out a list of the PCI devices that linux sees.  I'd be curious to see if the same message show up.

---

### Post by PeterJS on 2008-02-22
I'd be willing to bet that when you pin it down it's a graphics card. ATI and Nvidia cards don't take kindly to random PCI probes before their drivers are loaded, it's not a problem, by the time you've got an interactive system and a chance to do anything about it the drivers are loaded and it's taken care of.

---

### Post by Redrazor39 on 2008-02-22
ok, it's asking me for my password so I'm scared to do sudo Ispci (sorry I'm such a noob; I don't want to screw this up)

but I have an nvidia geforce go 7400 and the restricted driver installed

---

### Post by PeterJS on 2008-02-22
You can run lspci without sudo. What lspci does is **l**i**s**t the contents of the **pci** bus, it should never modify any files. So it's not necessary to run lspic with sudo, but it's not going to hurt. Generally when you see ls in the name of a program if it's a standard tool you can be safe knowing that it's short for list.

---

### Post by Redrazor39 on 2008-02-22
Thanks, that makes me feel better. Ok, I did it, and it spit out a bunch of stuff suddenly. Here it is:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
09:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

---

### Post by PeterJS on 2008-02-22
yeah that's exactly what lspci is supposed to do. This is probably the device in question:
```

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)

```
If you reboot and keep a sharp eye on it I'd bet that the PCI address given is 00:01.0.

---

### Post by Redrazor39 on 2008-02-22
so then what do I do to fix it?

---

### Post by PeterJS on 2008-02-22
You don't do anything. By the time you have the oppertunity to do anything it's already been fixed automatically.

---

### Post by Redrazor39 on 2008-02-22
so I just can't fix it at all? Do you think it will be fixed by hardy? when can I expect this fixed?

What does this error even mean?

---

### Post by PeterJS on 2008-02-22
It means that you video card is rejecting random probes of it's address space. Most video cards don't allow probes of their memory until after their driver is loaded and tells them that it's OK to let the OS look around.

And by fixed, I mean it's fixed right this very second as you're posting, if it wasn't you wouldn't have any VRAM, and likely as a consequence of that no picture on your screen. When you very first start up the kernel does a probe of the hardware to see if anything has changed, your video card rejects the portion of the probe trying to get to the VRAM but answers back well enough to be identified for the purposes of the hardware check. Then a few seconds later (if that) the driver for the card is loaded and unlocks it for the system to use, and a few seconds later (if that) you get the nice boot up splash screen, and your system is off and running.

---

### Post by Redrazor39 on 2008-02-22
Great! So nothing's wrong! Thank you so much!

But is there a way to get rid of this message or to alter the video card so it allows probes of its memory? Is there a risk to allowing probes of the memory?

Thank you so much for your help! I love the ubuntu forums!

---

### Post by PeterJS on 2008-02-22
No idea on disabling the message, trying to alter the video card I don't think is going to be workable, This is one of those things that's burned in to the ROMs on the card. I guess if you're a (really) really good hardware hacker, you could figure out what the rom does, program your own eprom do do mostly the same thing and then replace it, but that's the sort of thing legends are made of.

As for security, I don't think it poses any risk to you, now the manufactures clearly disagree on this point, hence why they do it, and I can see it being an issue of trade secrets for them if the OS just went randomly sniffing around their hardware with out their code in place to watch over things and keep the OS from looking at things they don't want it to see.

---

### Post by Redrazor39 on 2008-02-22
Ok. I can't hack for beans. So, what you're saying is just try to ignore it?

(At least now I know what's going on and that nothing's wrong)

---

### Post by PeterJS on 2008-02-22
Pretty much. I was trying to convey that it's theoretically possible, but not the sort of thing that anybody would ever do.

---

### Post by Redrazor39 on 2008-02-22
Thank you so much for your help.

---

