---
title: "HP Stream 11 ...Why do some distros work but not others?"
date: 2015-12-14
forum: General Help
---

### Post by pchokola on 2015-12-14
I am trying to find out what is so special about Lubuntu or Mint that allow it to boot perfectly on my laptop, while Clonezilla (Even their Ubuntu based version will not boot).  I don't know if it is a BIOS setting, kernel switch, etc., that I need to set).  I want to image the drive before I start deleting and modifying things on the laptop.


My setup:

[COLOR=#555555][FONT=sans-serif]HP Stream Notebook (Model: 11-r010nr 11.6").  This is HP's current model.
[/FONT][/COLOR]Various distros loaded onto a usb stick [COLOR=#555555][FONT=sans-serif](Sandisk Extreme USB 3.0) using YUMI software [/FONT][/COLOR][COLOR=#555555][FONT=sans-serif](2.0.1.9).

[/FONT][/COLOR]**What works:**
[COLOR=#555555][FONT=sans-serif]Lubuntu 15.10
[/FONT][/COLOR][COLOR=#555555][FONT=sans-serif]Mint 17.3

**What does NOT work**:
[/FONT][/COLOR][COLOR=#555555][FONT=sans-serif]clonezilla-live-2.4.2-61-i586.iso[/FONT][/COLOR]
[COLOR=#555555][FONT=sans-serif]clonezilla-live-2.4.2-61-amd64.iso[/FONT][/COLOR]
[COLOR=#555555][FONT=sans-serif]clonezilla-live-20151012-wily-amd64.iso (Ubuntu version)
[/FONT][/COLOR][COLOR=#555555][FONT=sans-serif]Gparted 0.24.0-2
[/FONT][/COLOR][COLOR=#555555][FONT=sans-serif]Fedora 23-10[/FONT][/COLOR][COLOR=#555555][FONT=sans-serif]
[/FONT][/COLOR][COLOR=#555555][FONT=sans-serif]Kaspersky Rescue DIsk 10[/FONT][/COLOR][COLOR=#555555][FONT=sans-serif]
[/FONT][/COLOR]Every Puppy Linux version


[COLOR=#555555][FONT=sans-serif]Now, just to get the USB to be recognized on the HP stream I had to make the following changes in BIOS:[/FONT][/COLOR]
[COLOR=#555555][FONT=sans-serif]Legacy Support = Enabled
Secure Boot = Disabled
Boot Order = USB First.[/FONT][/COLOR]
[COLOR=#555555][FONT=sans-serif]I have tried all many of the various menu switches to OS's before booting like graphics resolutions, etc., but they have not helped.

Also, importantly. every distro on that USB stick works on my OTHER computer which is a desktop, so this issue is specific to the HP Stream.[/FONT][/COLOR]

---

### Post by Dreamer Fithp Apprentice on 2015-12-14
I hesitate to ask, but just to be sure, since you specified "live" on several of the OSs that booted but not on the 2 that did: Are all of these, both the 2 that boot and those that don't, being tried from the same kind of media in the same drive? Like, for example, all were on CD and you attempted to boot all of them in the same CD drive?

---

### Post by pchokola on 2015-12-14
> **Dreamer Fithp Apprentice said:**
> I hesitate to ask, but just to be sure, since you specified "live" on several of the OSs that booted but not on the 2 that did: Are all of these, both the 2 that boot and those that don't, being tried from the same kind of media in the same drive? Like, for example, all were on CD and you attempted to boot all of them in the same CD drive?

All the distros are on the same USB stick noted above.  YUMI allows you to pick the distro you want to boot.  It remained in the same USB port and I just rebooted the laptop to reload YUMI to load another distro.

---

### Post by Dreamer Fithp Apprentice on 2015-12-15
I figured that was what you meant but I wanted to be sure the easiest answers were definitely eliminated.

Several things come to mind that you might want to consider.

If the main objective is to image the drive, it might be quicker to do it another way than it will be to find out what kind of HP weirdness is causing the problem. For example:

1- You could boot either the Lubuntu or the Mint and then install fsarchiver in the live system. You install software in a live system the same way you do on a regular spinning rust based system. Fsarchiver can easily do what you want.

2- There are other imaging programs you could do the same with. An uber-geek might use something like dd. It is even possible, at least in theory, to install Clonezialla to one of those booted live systems. There used to be, and presumably still are, directions on how to do that at the Clonezilla site. It ain't easy though. Fsarchiver IS easy.

3. You could try burning just Clonezilla to a flash drive or, perhaps better, if it is an option, a CD of it's own and see if that works without introducing the complication of YUMI.

4. You could take out the HD and put it in your other box and image it there, then return it.

Personally, I'd go for #1, by far the easiest.

On the other hand if imaging is secondary, and your main objective is to figure out why this is, just for curiosity or education, there might be tricky ways to get at the logs, despite the fact they are live systems. You don't say where in the boot process they fail. An exact description could be helpful. If you can get a tty, you can read those logs, if only with cat. The ones most likely to be of interest would be in /var/log, starting with bootlog, syslog, and kern-log.

I'm curious what your other box is. My only experience with HP was a nightmare and I'll never buy another one. They shipped with XP and it crashed every 30 minutes or so, giving spurious error messages. They were AWARE of the problem and suggested I buy Vista. Naturally they blamed MS, but MS didn't sell me a doorstop alleged to be a computer, HP did. Never again.

---

### Post by sudodus on 2015-12-15
We need more information to understand the problem.

- Is your computer running in [UEFI mode or BIOS mode](https://help.ubuntu.com/community/Installation/FromUSBStick#Test_if_running_in_UEFI_mode)?

- How do the 'other' distros fail to boot? Please describe in detail what happens with Clonezilla - what you see and what you hear :-)

- Have you tried to make a USB drive bootable with some other method? For example with [mkusb](https://help.ubuntu.com/community/mkusb), which does not make multiboot pendrives, but which makes very reliable booters, particularly the live-only systems - provided there are hybrid iso files, (and the Clonezilla iso files are hybrid iso files).

***Edit:*** I checked with a current Clonezilla iso file - clonezilla-live-2.4.2-61-amd64.iso, and mkusb can make a USB boot drive from it.

---

### Post by sudodus on 2015-12-15
> **Dreamer Fithp Apprentice said:**
> ...

If the main objective is to image the drive, it might be quicker to do it another way than it will be to find out what kind of HP weirdness is causing the problem. ...

I think this is a good observation. Some HP computers are tricky to boot, and it makes a difference how the USB boot drive is made, so try different tools (not only YUMI).

---

### Post by pchokola on 2015-12-15
Thanks for the detailed replies.  I will try one of those methods when I get a chance.  In the meantime I made a Windows image backup.  The issue with that, is it doesn't backup the sdhc drive, where I am installing applications because the main drive of the Stream is only 32 GB.  I have an external usb CD drive at home that I would try, but I am out of state taking a Red Hat Sys Admin / Cloud Computing class and don't have access to it.  

You asked about my desktop...It is a home made system running Centos 7, Centos 6, Linux Mint Debian (LMDE) and Win 7.  Like I said, every OS on the USB runs perfectly on that computer.  I did haul the desktop with me; that is why I bought the Stream...I needed something cheap and portable while my desktop is packed away in  my car and I move to the next location to look for or start a job, wherever that may be.

---

### Post by pchokola on 2015-12-27
SOLVED.

So, this was really bothering me, so Iplayed around with it this morning a bit. It was recommended by the Clonezilla author that I try Tuxboot and/or another USB drive brand. So first I tried Tuxboot with Clonezilla 2.4.2-61 Stable andinitially it didn't work like all my other attempts.  However thistime I noticed a new boot option in the boot menu:


Whereas the onlyboot option before was:


USB Hard Drive -Sandisk Extreme......


A new entry appearedwhen using Tuxboot, and with Clonezilla being the only ISO on the USBdrive:


USB Hard Drive (UEFI) -  Sandisk Extreme


So, I gave it a tryand a slightly different Clonezilla main menu popped up.  It was aplain text menu of the normal selection of choices (resolution, etc)rather than the normal scrollable menu.  Also, on top of the screenwas the following text...."GNU grub version 2.02 Beta 2-28". I selected one of the entries (1024 resolution in my case) andClonezilla started up properly.  Unfortunately no such option exists when running YUMI, so I would have to put each individual distro on its own USB stick, which of course I would never do.

---

### Post by sudodus on 2015-12-27
Congratulations :KS and thanks for sharing your solution :-)

-o-

There are multiboot systems, that work also in UEFI mode, I think you can try ***Multisystem***.

An alternative is to*** consider the USB pendrive to be a temporary device***. Store the iso files in your 'production computer', and {copy/clone/flash/burn/restore} the current iso file to the drive and make a live-only boot drive. It takes only 2-3 minutes with [mkusb](https://help.ubuntu.com/community/mkusb), and you get a boot drive, that is very reliable in UEFI mode as well as in BIOS mode, if the system in the iso file is prepared for it. All current Ubuntu iso files as well as all iso files of the major linux distros are 'hybrid iso files', and work that way.

---

