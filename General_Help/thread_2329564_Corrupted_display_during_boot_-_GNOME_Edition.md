---
title: "Corrupted display during boot - GNOME Edition"
date: 2016-07-03
forum: General Help
---

### Post by guardianin on 2016-07-03
I'm having some trouble with Ubuntu. Kindly note that I am a newbie to Linux. This is my hardware setup:
 
MSI AM1 motherboard: [https://www.msi.com/Motherboard/AM1I.html#hero-overview](https://www.msi.com/Motherboard/AM1I.html#hero-overview)
Processor: AMD Sempron APU 2650 1.45 Ghz with Radeon R3 graphics
RAM: Corsair 4 GB DDR3 (single stick)
 
I have installed Ubuntu GNOME 16.04 after a few tries. The issue I faced during installation and the one I face during boot is a corrupted display. I have to turn off / reset the system multiple times before it works. I have updated it fully after installation, and also installed a proprietary AMD driver that was under the Additional Drivers section.
 
I get the GRUB boot screen below:
[ATTACH=CONFIG]269920[/ATTACH]

After I select Ubuntu, I get this:
[ATTACH=CONFIG]269921[/ATTACH]


No amount of turning off / resetting helps. Just not able to go past the corrupt display!

Please help!

---

### Post by RobGoss on 2016-07-03
[FONT=Ubuntu][COLOR=#111111]Hello and welcome to the forum, This looks like a** driver** issue to me this post might help you with this issue 
[/COLOR][/FONT][http://askubuntu.com/questions/460591/ubuntu-14-04-screen-corruption-on-live-desktop-amd-7970](http://askubuntu.com/questions/460591/ubuntu-14-04-screen-corruption-on-live-desktop-amd-7970)

---

### Post by guardianin on 2016-07-03
Thanks! I went through the link you gave. During the last session when it had successfully booted, I had checked in the Additional Drivers section, there was only 1 processor driver listed, which I installed.

I have tried the nomodeset option. It made no difference. Of course, it could also be due to me not having entered it correctly as I am not very familiar with Linux.

---

### Post by RobGoss on 2016-07-03
> **guardianin said:**
> Thanks! I went through the link you gave. During the last session when it had successfully booted, I had checked in the Additional Drivers section, there was only 1 processor driver listed, which I installed.

I have tried the nomodeset option. It made no difference. Of course, it could also be due to me not having entered it correctly as I am not very familiar with Linux.


Is this a fresh installation of** Ubuntu 16.04**? Have you try installing Ubuntu again to see if this issue persist sometimes problems will work there way out on a second installation if it continues maybe we can figure out why and try and get it corrected.

Are you able to boot to your desktop?

---

### Post by guardianin on 2016-07-03
Yes, completely fresh installation. I was able to boot once in the morning. Just can't boot now, same screen every time. I've also tried to go into the Live environments of Fedora and Mint, same issue. Shows me that corrupted screen straight after selecting any option with any distro.

I've also tried the nomodeset option, no luck!

---

### Post by RobGoss on 2016-07-03
Off hand do you know what internal graphic card chip your machine is using it may not be compatible with Ubuntu

---

