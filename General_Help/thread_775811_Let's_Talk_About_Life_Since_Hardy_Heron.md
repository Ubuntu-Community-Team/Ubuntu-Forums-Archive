---
title: "Let's Talk About Life Since Hardy Heron"
date: 2008-04-30
forum: General Help
---

### Post by PopeMatt on 2008-04-30
So, as a rule, I don't test beta distros, because I only have one partition and not enough room to make another viable. So I was psyched when Hardy went standard, because I hadn't seen it yet.
Since then, my PC has been taken over by aliens.

Problem 1: Ridiculously slow times on all things GUI.
This was impossible to live with, and I eventually found the fix, which had to do with ATI drivers. Okay, dealt with. This is the only solved problem.

Problem 2: Firefox. Shoot me.
  2 a. Firefox crashes. I gave up on this, uninstalled FFbeta3, and reinstalled FF2. Who the hell thought it was a good idea to include a beta browser as the STANDARD in a LONG-TERM SUPPORT distro?
  2 b. Flash runs slow and has iffy sound. The sound is temporarily solved by running a pulseaudio command that I found somewhere. Flash runs too slow to play HeliAttack3. This is a HUGE problem for me. Please help.
  2 c. Cannot install extensions in FF2. I saw that someone else had this problem, and the solution involved deleting FF3b and your profile, then reinstalling FF2. Didn't work. Although, when that person tried to install an extension, they were getting error 230. I'm getting error 203. Hi, I miss stumbleupon. Please help.

Problem 3: SCREENSAVER OF DOOM +5: Unholy Avenger (only usable by chaotic evil programmers of twelfth level or higher)
Okay, so whenever I leave my computer for fifteen minutes, screensaver comes up. That works. But the screensaver (currently electricsheep) runs REALLY slow, which makes it ugly. But also, when I take it out of the screensaver, my computer becomes unusable. Windows are weird sizes, I can only use them for a moment, and only see part of them. It's hard to explain, but I can't save anything I was working on and I have to do a CTRL-ALT-Backspace. I have had to turn off my screensaver, which consequently means anyone can use my computer if I'm not in the room. I don't trust my roommate. He's a dick. Please help.


Those are the issues I'm dealing with at the moment. Hey, Ubuntu team... WHAT THE HELL?!

Sorry, I didn't mean that. I still love you, but please help me reclaim my PC.

--Matt

---

### Post by PopeMatt on 2008-04-30
Ka-BUMP

Help, in the name of all that is good and just and holy and bright and pretty!

---

### Post by lswest on 2008-04-30
Well, if Gutsy works for you, i'd say the easiest fix would be to go back to Gutsy.  Otherwise, yeah, post information about what graphic card you have, etc. and we might be able to help you.  ```
lspci
lshw -C Display
``` would be a good place to start.

*Edit* also, giving a more descriptive title would help, and maybe a separate thread per issue would be a good way to ensure you get replies

---

### Post by aheckler on 2008-04-30
To fix your 203 error in Firefox, try this: [http://kb.mozillazine.org/Unable_to_install_themes_or_extensions_-_Firefox#Corrupt_extension_files](http://kb.mozillazine.org/Unable_to_install_themes_or_extensions_-_Firefox#Corrupt_extension_files)

---

### Post by PopeMatt on 2008-04-30
Sorry about the indescriptive title. I was flustered.
Thanks for the 203 fix, worked great.
I would revert to Gutsy, but as far as I've read, it can't be done without doing a fresh install, which I'd like to avoid.

lspci output:
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
03:03.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)
03:04.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
03:06.0 Ethernet controller: Intel Corporation 82541GI Gigabit Ethernet Controller

lshw -C Display output:
  *-display               
       description: VGA compatible controller
       product: RV370 5B60 [Radeon X300 (PCIE)]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: driver=fglrx_pci latency=0 module=fglrx

---

### Post by lswest on 2008-04-30
the laggy flash is probably caused by the graphic drivers, how did you install them? (the lshw output tells me it's using restricted drivers, so i assume you either enabled the restricted drivers, installed it via envy, or did it by hand)

the sound issue has been addressed a few times here i think, if you give the forums a search for "flash pulseaudio hardy" you might get something to help you out there, otherwise, that's not something i can likely help with.

Again, the screensaver seems to be an issue with the graphic card drivers.

---

### Post by PopeMatt on 2008-04-30
I installed the ATI drivers from their website by hand, which made it better than it was immediately after upgrading.

The flash sound isn't an issue, I was just pointing it out in case it was related to something else.

Also, whenever I click on a web link from a non-browser application, it no longer opens it in the browser. How can I fix that, anyone?

---

### Post by themisanthrope on 2008-05-01
> **PopeMatt said:**
> Who the hell thought it was a good idea to include a beta browser as the STANDARD in a LONG-TERM SUPPORT distro?

--Matt

Who the hell indeed?! You put it much more mildly than I would have.

---

### Post by Cadmus on 2008-05-01
I notice FF3's been in beta a while, do you reckon there was a belief that it would be finished before Hardy was ready for release? Though one assumes things will level out with a simple update once FF3 is released proper.

---

### Post by danwood76 on 2008-05-01
@Off topic

I think FF3 is a good idea, it works perfectly.
There are a few people with issues, but I prefer it to FF2.

Also the final FF3 will be out in June and Hardy Heron 8.04.1 will be out in July obviously with the full version.

@The OP

I think most of your issues are graphics driver related, do you have compiz running at all?
Try switching it off and see if it speeds things up.

What are your full system specs?
(CPU, RAM, etc)

---

### Post by Fixman on 2008-05-01
> **PopeMatt said:**
>  
Problem 1: Ridiculously slow times on all things GUI.
This was impossible to live with, and I eventually found the fix, which had to do with ATI drivers. Okay, dealt with. This is the only solved problem.


Then don't moan

> 
Problem 2: Firefox. Shoot me.
  2 a. Firefox crashes. I gave up on this, uninstalled FFbeta3, and reinstalled FF2. Who the hell thought it was a good idea to include a beta browser as the STANDARD in a LONG-TERM SUPPORT distro?
  2 b. Flash runs slow and has iffy sound. The sound is temporarily solved by running a pulseaudio command that I found somewhere. Flash runs too slow to play HeliAttack3. This is a HUGE problem for me. Please help.
  2 c. Cannot install extensions in FF2. I saw that someone else had this problem, and the solution involved deleting FF3b and your profile, then reinstalling FF2. Didn't work. Although, when that person tried to install an extension, they were getting error 230. I'm getting error 203. Hi, I miss stumbleupon. Please help.


Uninstall the packages "firefox" and "firefox-3.0". Then delete the $HOME/.mozilla folder

> 
Problem 3: SCREENSAVER OF DOOM +5: Unholy Avenger (only usable by chaotic evil programmers of twelfth level or higher)
Okay, so whenever I leave my computer for fifteen minutes, screensaver comes up. That works. But the screensaver (currently electricsheep) runs REALLY slow, which makes it ugly. But also, when I take it out of the screensaver, my computer becomes unusable. Windows are weird sizes, I can only use them for a moment, and only see part of them. It's hard to explain, but I can't save anything I was working on and I have to do a CTRL-ALT-Backspace. I have had to turn off my screensaver, which consequently means anyone can use my computer if I'm not in the room. I don't trust my roommate. He's a dick. Please help.


Do your drivers work?

---

### Post by Voxan on 2008-05-02
> **PopeMatt said:**
> I have had to turn off my screensaver, which consequently means anyone can use my computer if I'm not in the room. I don't trust my roommate. He's a dick. Please help.

Hi, this is not a way to fix your problems (as I have some too that I can't solve), but this will help you to protect your PC.
When you leave your PC unattended, press this:
Ctrl-Alt-L
This will lock your screen and you need to enter your password to access the OS again. It also turns your screen black (probably save power).
Good luck.

---

### Post by PopeMatt on 2008-05-02
I am running compiz, but turning it off changes nothing. Same issues.
Also, my VLC hotkeys no longer work. Tried deleting .vlc folder. Didn't work.

---

### Post by danwood76 on 2008-05-02
Have you got XGL running?
(package xserver-xgl installed)
I have read a lot of people have this package installed and its not necessary.

If you do uninstall it and see if it makes a difference.

---

