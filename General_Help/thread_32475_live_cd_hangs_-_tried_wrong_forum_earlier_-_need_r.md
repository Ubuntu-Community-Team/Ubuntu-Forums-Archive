---
title: "live cd hangs - tried wrong forum earlier - need resolution"
date: 2005-05-07
forum: General Help
---

### Post by hambone on 2005-05-07
My system>
Gateway E-1800, Intel Celeron 1.2Ghz, 512MB memory
40GB WD HDD, Memorex DVD+/-RW optical, Memorex 52Max CD/RW optical(boot)
PCI VisionTek Xtasy Nvidea GeForce2 MX/MX 400 graphics card (on board video disabled)
PCI Belkin USB 2.0 card
PCI 10/100 Ethernet card for DSL in place of my old standard modem card (no more PCI slots) 
Speedstream 5100 DSL ethernet external modem
USB soundblaster device (onboard sound disabled)
USB HP psc 1350 all-in-one printer, scanner, copier
USB San Disk Image Mate memory stick RW
Microtek 710S 17" LCD display
OEM Windows XP Home Edition, SP2 :-x 

I verified my download with winMD5sum.  I used Isorecorder V2 to copy the download to a CDr and it does start the boot process.

The problem I am having with the install is the same as was described in another thread in the main installatiion forum, but it seems to be dead now.   So here's the fresh info:  The default install detects all my hardware, makes it to the boot screen and then displays the following:

Starting Ubuntu... 
* version 2.86 booting 
* Mounting a tmpfs over /dev... [ ok ]
* Creating initial device modes... [ ok ]
* Setting disc parameters... [ ok ]
* Setting the System Clock using the Hardware Clock as reference… [ ok ]
* Cleaning up ifupdown… [ ok ]
* Calculating module dependencies… [ ok ]
* Loading modules… [ ok ]
* Creating device-mapper devices… [ ok ]
* Starting RAID devices… [ ok ]
* Setting up LUM Volume Groups… [ ok ]
* Starting Enterprise Volume Management System… [ ok ]
* Checking all file systems… [ ok ]
* Mounting local filesystems… 
tmpfs on/tmp type tmpfs (rw,nosuid,nodev) 
* Running 0dns-down to make sure resolv.conf is ok… [ ok ]
* Initializing ifupdown state… 
* /dev/shm/network/… [ ok ]
* Reading desktop files… [ ok ]
* Starting hotplug subsystem… [ ok ]
* Configuring network interfaces… [ ok ]
* Setting up general console font… 
* Setting the System Clock using the Hardware Clock as reference… [ ok ]
* Synchronizing clock to ntp.ubuntulinux.org… 
[COLOR=Red]*[/COLOR]ror : Temporary failure in name resolution [[COLOR=Red]fail[/COLOR]]
* Initializing random number generator… [ ok ]
* Setting up X server socket directory… [ ok ]
* Setting up ICE socket directory… [ ok ]
* Entering runlevel: 2 
* Starting system log daemon… [ ok ]
* Starting kernel log daemon… [ ok ]
* Setting up ALSA… 
* Starting GNOME Display Manager… 
* Starting Common Unix Printing System: cupsd [ ok ]

After a less-than-a-second pause, the screen blanks and then displays a static and unmoveable cursor, top left corner. Waiting 30 minutes did not produce a timeout. The system was locked tight with no keyboard function and the CD went on spinning. I could not remove it by using the eject button.  I pressed and held the computer power button for 8 seconds to shut everything down.

I tried the boot-up several times and alternately removed various hardware items (printer, card reader). I was watching the other message thread anticipating a resolution, but nothing...  :-? 

I am not a programmer and was hoping to just run the CD and start the Linux experience.  I am anxious to see what I have been missing without risking my existing OS.  Any help would be appreciated.  

Thank you. *M * 

(I wondered about Ubunto setting the system clock twice in the boot sequence and then failing when it tried to synchronize to ntp.ubuntulinux.org, but I don't think that is what is hanging it up.  Like I said, this problem was announced by another person before but, unless I missed something, hasn't been addressed.  Sorry if it has, and I would appreciate a link to the answer.  :grin:  )

---

### Post by hambone on 2005-05-09
Thanks anyway...

The original problem, as described by another guest on April 22, is still unresolved for me (and him?) and remains unanswered in both threads that I watch.  In the meantime, I searched google for answers and found none.  But I did find another option.

I downloaded a different distro (initials, Sm) and it ran like a champ on my system without any intervention or prodding.  Was up all night having the Linux experience for the first time.    \\:D/   Only downside is I can hardly stay awake today. 

I'm calling [COLOR=DarkRed]No Joy [/COLOR] on Umbunto.  Thanks to all who read this thread - but I suspect it was mostly me, checking back. 

Good luck, friends.

---

### Post by MartinJ on 2005-05-31
I am having the exact same problem as hambone - temporary failure in name resolution.
Laptop specs are:

IBM Thinkpad R32 (2658-MNG)
Pentium 4 1.7 GHz
768MB RAM
TEAC DW-28E CD drive
ATI Mobility Radeon graphic card
USB mouse
network card connected to university LAN
no other hardware connected.

The problem is that the LiveCD worked last week.  I tried it several times today with no success.

Any help is greatly appreciated.

---

### Post by MartinJ on 2005-05-31
I'm writing this from Ubuntu :)

Whenever I restarted from Windows without switching off the computer the problem occured.

I shut down Windows fully and turned off the computer.  Then I switched it back on to boot the live cd, Ubuntu loaded perfectly.

---

### Post by abc on 2005-11-09
reply to ror: temporary failure in name resolution
hi,
when you run the live cd, at some point you will be asked to select the desired x server driver, if you don't chose the right driver then you will get
the above error.

---

