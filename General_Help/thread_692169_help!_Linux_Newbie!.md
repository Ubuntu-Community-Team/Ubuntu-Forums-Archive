---
title: "help! Linux Newbie!"
date: 2008-02-09
forum: General Help
---

### Post by patree on 2008-02-09
hello ubuntu forums. 
this is my first post on here, and i am a very new member, as i just got linux for the first time last night. It is all very fun and exciting but I am so lost! It was kind of a spur of the moment thing to get linux but i am excited to learn and very sick of using windows. Anyways! here are my main problems for now, listed in order of priority to me.

1) No sound! i have managed to make videos work, and get flash player installed, but there is not a single sound coming out of my speakers.

2) When I update there are some files called Cupsys. I had to re-install linux 3 times, because everytime i did the install updates cupsys would fail, and my linux would for some reason be demolished... so for now i am just scared to update.

3) There is a strange message when i start up Ubuntu that says BIO BUG 81 FOUND  or something along those lines... so far it has not caused me any problems...

thats all for now i guess... Thank you to anybody who tries to help out. please remember im really new to ubuntu so clear explintions would help :)

---

### Post by Zeroangel on 2008-02-09
Hey and welcome to the ubuntu forums. Ubuntu doesnt always play well with all hardware for reasons often attributed to lack of manufacturer support. If any flakiness/instability occurs out of the box it is usually for that reason and its likely you can get everything running by doing a few hacks.

For starters. Please post as much information about your hardware as you can, including:

Motherboard model (ie: ASUS A7V333-X)
Videocard
Sound card
Amount of RAM installed
Any other special information or circumstances (ie: you've downloaded a 64-bit ubuntu or something like that)

Unless your components are very rare, then chances are someone else had a similar problem and might be able to help you (or you'll be able to search the forums for posts related to your problem)

P.S.: Cupsys is just used for managing your printer drivers (the printer backend is called CUPS). If cupsys doesnt work or is uninstalled, you wont be able to use the default print functionality. This normally should not cause your system to fail, chances are that theres a larger issue here that we need to investigate.

---

### Post by jan quark on 2008-02-09
first patree I welcome you to the ubuntu community

good enough small talk :)
 
> 
1) No sound! i have managed to make videos work, and get flash player installed, but there is not a single sound coming out of my speakers.

type in into the terminal ( can be found here: accessories > terminal)

```
lspci  
```

and post the output here
lspci is a utility for displaying information about all PCI buses in the system and all devices connected to them.

if you want to get some more info about a command you are using type into the terminal

```
man command
```

this will display a manual explaining the command
you can leave the manual pressing the 'q' key


> 2) When I update there are some files called Cupsys. I had to re-install linux 3 times, because everytime i did the install updates cupsys would fail, and my linux would for some reason be demolished... so for now i am just scared to update.

cupsys is a Common UNIX Printing System, 

if you want to know something about a specific package just open the symantic package manager system > administration > synaptic packet manager and type the package name into the search field then click on the displayed results and additional info will be displayed at the bottom of the window

you can also lock a specific package to not be updated anymore by clicking on the package and going to edit > lock package version

> 

3) There is a strange message when i start up Ubuntu that says BIO BUG 81 FOUND or something along those lines... so far it has not caused me any problems...



concerning the  BIO BUG 81 FOUND I have no idea :lolflag:
nobody is perfect

---

### Post by ajgreeny on 2008-02-09
I suspect the error message you get is something like:-
**MP-BIOS bug: 8254 timer not connected to IO-APIC**
but if the computer still boots OK, I shouldn't worry too much.  It has always appeared on my wife's Acer Travelmate 2100 laptop, but has never stopped anything working except maybe suspend or power management in some form, though it has never really been a disadvantage to her, and everything else works fine.

As for the cupsys problem, that really baffles me, and I can see no real reason for that to crash the whole system as it is simply the printing system software.

---

### Post by patree on 2008-02-09
Wow thanks for the quick responses! i dont know if this is exactly what you wanted but heres what happened when i typed it in...

patree@epicwin:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)


About my computer: 
its a Compaq Presario V3000
Intel Core Duo T2400 1.83 GHz
It came with 512MB RAM but i upgraded it to 2GB
nVidia Graphics card

I wish i knew more about the specifics but i dont know how to check them on linux Lol :oops:

---

### Post by patree on 2008-02-09
bump

---

### Post by Zeroangel on 2008-02-09
Well, support for your onboard sound should have came with the Ubuntu Feisty 7.04 release -- and we are now using the Gutsy 7.10 version. So this is strange that it doesn't work (I'm also assuming that you are using Ubuntu 7.10)

OK. Try opening the **Restricted Drivers Manager** (its located in the System Menu -> Administration). If you see any options to enable any of the drivers, do so, then restart your machine.

As far as the BIO BUG is concerned, just try to write down the exact number in the error. This might be a clue as to why everything doesn't work. Also when your computer is booting into Ubuntu press alt+f2 and watch the terminal output. Make sure to write down anything that [FAIL]s

---

### Post by patree on 2008-02-10
ive been working on this all night and have had no luck at all... 

im on 7.10
all restricted drivers are on and working.
my system recognizes my sound cards, just .. no sound?
all volumes are up, including in the alsamixer

the BIOBUG is #81, i still dont know what it means

ugh im  /sooo/ frustrated

---

### Post by knutschr on 2008-02-10
For the sound problem, there is an exellent guide here you might try:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Zeroangel on 2008-02-10
I dunno how much time u put into your Ubuntu install have you tried other Linux distros like PCLinuxOS, Fedora Core, or Mepis? They might like your hardware better (but its doubtful).

> **patree said:**
> ive been working on this all night and have had no luck at all... 

im on 7.10
all restricted drivers are on and working.
my system recognizes my sound cards, just .. no sound?
all volumes are up, including in the alsamixer

the BIOBUG is #81, i still dont know what it means

ugh im  /sooo/ frustrated
I did some looking around and where there is the BIOS BUG #81 its usually a sign that something in your motherboard uses a very non-standard way of doing things that Linux doesnt like and it foreshadows problems. Thats too bad your laptop doesnt like linux very much.

Some users have suggested turning off some of the things like APIC in the grub menu using options and stuff. I'm too lazy right now to look how to do that so you are going to have to do that yourself.

---

### Post by patree on 2008-02-10
hey!
Thank to everybody that has tried to help.
last night while up until 4AM trying to fix this problem i managed to dig deeper into my terminal then i should while following a guide, and ended up destroying my linux again! haha

well i reinstalled it (for the fourth time) and magically THERES SOUND! woot lol

although there is still a bio bug 81... 
for now i am pretty happy that i can enjoy music video etc. and get to customizing my new desktop :)

---

### Post by ed-koala on 2008-02-10
I found something on the web about your Bio error.  Not sure how applicable it is, but seems to be. No solution is found there, but you might find it informative.  Here's the link

[http://www.mepis.org/node/10817]("http://www.mepis.org/node/10817")

---

### Post by Zeroangel on 2008-02-11
Aww man, how did you manage to destroy it this time?

Well anyways its good for you that your sound works now. Next time if you destroy it, maybe try out a different distro and see if it sticks. Because it seems ubuntu doesnt like your particular laptop if it does that so often.

---

