---
title: "Grub disappeared, unable to boot"
date: 2014-04-06
forum: General Help
---

### Post by aymon on 2014-04-06
Hello there,

As the title says, I'm stuck unable to boot into any of my OS's. My initial ubuntu install broke my windows install which I sorted out with boot-repair. I occasionally used to get this grub disappearing issue previously but I'd simply boot into my live usb and run boot-repair again which would fix things. 

Today this happened again although this time something happened to my live usb and it would give me some kind of syslinux error when trying to boot from usb. I'm now stuck unable to boot into either windows or ubuntu without any form of media to repair my boot. Booting into windows brings up a 'boot selection failed because a required device is inaccessible message'. 

I had one way of getting my computer back and that was my recovery drive however following the advice of one user to try to recover my windows mbr with bootsect.exe has closed off that avenue as well as it gives me the exact same message as when I tried to boot windows 7. 

I am am now stuck without any cd or usb to repair my boot and no way to restore my computer that I know of. If anyone could please help me it would be greatly appreciated. I have no other computers at my disposal except for work ones on which webmarshall blocks super grub disk from being downloaded.

sorry for the rudimentary post. I'm trying from an iPhone and pulling my hair out simultaneously.

---

### Post by grahammechanical on 2014-04-06
Please describe what you see on the screen when the machine tries to boot. That information may point in the direction of what the fault is.

Regards.

---

### Post by aymon on 2014-04-06
Black screen titled Windows Boot Manager. 

The boot selection failed because a required device is inaccessible. Error 0x000000f

I don't even get the option to boot into my ubuntu install it goes straight to windows.

---

### Post by Bashing-om on 2014-04-06
aymon; Hello, Welcome to the forum.

Bad stuff does happen, regretful you are taking your share now.
Windows 7 sometimes means UEFI booting control ? Is that the case here ? Have you made sure that the device to boot the liveUSB is selected correctly ?

Without a liveDVD/USB or some means to boot to get to the install's ubuntu partition, there is not a thing that can be done.

The need is to fix the MBR for ubuntu as Windows will not cooperate with ubuntu. All I can suggest is to find a means to download an .iso file :
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
md5sum that .iso file, burn to DVD, verify the disk and ->

boot-repair can also be burned to be bootable:
[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/) 
boot up the liveDVD OR boot-repair and re-install grub.

[INDENT][INDENT]sometimes one has
[INDENT][INDENT][INDENT]back up and punt
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aymon on 2014-04-06
> **Bashing-om said:**
> aymon; Hello, Welcome to the forum.

Bad stuff does happen, regretful you are taking your share now.
Windows 7 sometimes means UEFI booting control ? Is that the case here ? Have you made sure that the device to boot the liveUSB is selected correctly ?

Without a liveDVD/USB or some means to boot to get to the install's ubuntu partition, there is not a thing that can be done.

The need is to fix the MBR for ubuntu as Windows will not cooperate with ubuntu. All I can suggest is to find a means to download an .iso file :
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
md5sum that .iso file, burn to DVD, verify the disk and ->

boot-repair can also be burned to be bootable:
[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/) 
boot up the liveDVD OR boot-repair and re-install grub.
[INDENT][INDENT]sometimes one has[INDENT][INDENT][INDENT]back up and punt
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Thank you for your reply. I have come to accept this fact now. I have asked a friend to send me an Ultimate Boot USB which should hopefully help me recover my ubuntu install. It is absolutely painful being without a PC at the moment but I guess no amount of staring at my bios and trying to find some sort of command line will help.

---

### Post by Bashing-om on 2014-04-06
aymon; Hey,

I feel for ya, I recently hosed up my system and have no liveDVD for the current install. I was fortunate that I had an old liveCD that I was able to work with to get my grub rebuilt. Even then was an iffy situation, but I did manage. You can bet that When 14.04 is released I will rectify that situation.

In your current predicament, with no ubuntu liveMedium, might be even iffier, once booted into the ubuntu install, and with confirmed internet connectivity, might consider purging the present grub and a (re-)install of grub - given the past history of booting issues.

one step at a time
[INDENT][INDENT]gets you there
[/INDENT][/INDENT]

---

