---
title: "Using Text Installation to bypass Kernel Direct Mapping issue?"
date: 2008-04-15
forum: General Help
---

### Post by FZE on 2008-04-15
Hello, I'm a first-time Linux user and opted for Ubuntu as my first distribution. After my Windows XP install disk continually failed on my new computer for unknown reasons, I got fed up with being without a main desktop for 2 weeks, and decided Linux would be my best option. After sorting out some confusion over the boot CD, I finally managed to burn one successfully, and boot on my main desktop. Unfortunately, as I've seen in other topics, I've encountered a recurring issue, in which the boot up halts directly after the phase...

```

Kernel alive
kernel direct mapping tables up to 100000000
```

I've tried several of the suggestions in those topics, and none have worked (such as removing 'splash' from the command line and entering commands such as 'noapic' and 'break=bottom'), and apparently the issue revolves around the graphical installation. What I want to try now is a text installation, but I'm unable to find a guide on it as conclusive as that for graphical installation. At the CD's boot menu, I can hit Esc and enter the Text Mode Interface, but, being a first-timer, I'm clueless as to how to proceed from there. 

Are there any guides, or even directions as to what to do next, that anyone knows of? I understand the text mode installation is readily available on the Alternate CD, but I'm afraid I'm fresh out of blanks, and it may be difficult to burn another in any reasonable timeframe. Alternately, are there any other solutions to the 'kernel direct mapping' issue I spoke of earlier? It's eerily similar to the problems I experienced with my Windows install, and I'm beginning to fear it's faulty hardware.

---

### Post by FZE on 2008-04-15
Well, scratch that idea. I just tried a text install with the Alternate CD on a blank DVD I found, it still hangs in the same place. If it's any help, further information on my system is as follows:

Current Hardware Status
Biostar TA770 A2+ motherboard
AMD Phenom 9550 CPU
1GB (Out of 2GB) Corsair Dominator RAM
eVGA GeForce 9600GT512-OC
Seagate Barracuda 320GB SATA HD

Plugged into the back of the computer:
- Power
- Monitor (DVI port 1)
- PS/2 Keyboard

I'm beginning to theorize that it's a problem with the video card. Across 3 separate drives, 4 separate disks, and countless BIOS configurations, both Ubuntu and Windows jam at what appear to be equivalent places, and both stem from an issue with APIC, as far as I can tell. Many potential solutions for my issues with Windows involved disabling APIC, which just makes my computer jam at Verifying DMI Pool Data and restart over and over, and potential solutions for the Kernel Direct Mapping Tables issue involve commands such as 'noapic'. This is extremely frustrating. Somehow the most modern computer I've ever owned is the hardest and most frustrating build I've ever done.

The only other thing I can think of to do right now is flashing my BIOS, but I have no functioning floppy drive. If it *is* the video card as I suspect, there's precious little I can do about it, with no other PCI or PCI-X video cards sitting around to work with. How maddening the last two weeks have been.

---

### Post by audacity on 2008-04-24
Hey man, I found a solution that worked in this thread:
[http://sudan.ubuntuforums.com/showthread.php?t=696795](http://sudan.ubuntuforums.com/showthread.php?t=696795)

seems the problem has to do with the splash screen and newer video cards not replying to certain queries, or something. 
Remove splash
Add vga=771
Really any vga mode should do, it forces the videocard into VESA mode. You might have to remove quiet as well, but it won't make much difference as nothing is displayed until the login screen, so don't panic. You'll know it worked when you see ubuntu's smiling face. Hope that helps!

---

