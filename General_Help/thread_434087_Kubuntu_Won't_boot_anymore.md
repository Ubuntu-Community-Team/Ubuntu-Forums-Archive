---
title: "Kubuntu Won't boot anymore"
date: 2007-05-05
forum: General Help
---

### Post by Crashing on 2007-05-05
I installed Kubuntu on another computer yesterday. Windows XP Home was already installed on a 95 Gb partition and I booted the live CD (Kubuntu 7.04 beta) Created a Swap partition an the other / partition. Everything installed right and I rebooted and installed all the updates to bring the system up to date. I'm glad I didn't have to make a separate FAT32 partition for the bootloader, GRUB pops up and asks me if I want XP or Kubuntu. The computer has been rebooted into both OSes multiple times and has worked fine until now. 
This install is on a P42.4 GHz, 700 something megs of RAM with an ATI Mobility Radeon 7500 graphics card. Windows still boots fine. When Kubuntu loads, I get a brief list of 3 errors, something about IRQ. the Splash screen comes up and the progress bar gets to the end. Once it's at the end, Half a screen of gibberish flashes on briefly and I can see some sort of error message before it goes away. The splash screen comes up again  and then I get this:
```
[some number] bcm43xx: Error: Microcode "bcm43xx_microcode.fm" is not available
[some different  number] bcm43xx: Error: Microcode "bcm43xx_microcode.fm" is not available
```
This will continue until I shut the system down.
Ideas?

Later:
Oh dear! this is much worse than I thought!!!!! I can't even boot in recovery mode for the updated kernel (something-15)!!! Aughh! I can only boot into the old kernel (something-12) and even then only the recovery mode works. Should I do a complete wipe?

---

### Post by Crashing on 2007-05-06
Buuuuuuuummmp....
Anyone?


Please....

---

### Post by strabes on 2007-05-06
That's an error related to your broadcom wireless card. I don't know how to fix it though since I've never really had to deal with those.

---

### Post by Crashing on 2007-05-07
Can I unplug it and then will it boot?
It's a Motorola PCMCIA card. When I tried to connect to my network, it didn't activate the card. Do I need to install a driver  for it to work?

---

### Post by Crashing on 2007-05-10
Anyone????

---

### Post by strabes on 2007-05-10
Did you try taking it out and booting? What happens?

---

### Post by Crashing on 2007-05-15
Still not working..... 
I can only boot my old kernel in recovery mode. I even tried booting from the live CD in graphics safe mode. I can't boot in the normal mode because while its in the middle of scrolling all of its gibberish, the screen slowly fades into a sky blue with an ooze effect. after that, I can hear startup sounds but that's useless if you can't see anything. The driver update function doesn't do anything either. It doesn't matter wether the wireless card is in or not. 
This is driving me crazy! I don't really want to re-install because I'd have to reinstall programs, firefox plugins, customize KDE again......

---

### Post by Crashing on 2007-05-16
Ok, I have an idea. Could someone tell me how to make the system NOT try to mount a wireless network on startup? this would have to be a command line deal.

---

