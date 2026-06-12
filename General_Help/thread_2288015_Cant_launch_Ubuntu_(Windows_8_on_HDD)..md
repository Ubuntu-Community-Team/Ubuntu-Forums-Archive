---
title: "Cant launch Ubuntu (Windows 8 on HDD)."
date: 2015-07-23
forum: General Help
---

### Post by hultongetty on 2015-07-23
Today I launched ubuntu from my Pendrive. Installed it, set Windows Boot Menager to 1st place in BIOS boot priority...
After instalation, ubuntu automatically rebooted and... Yeah...
My PC keeps launching Windows 8 which is located on the same HDD...
I set everything in BIOS, installed everything well but my PC ignores Linux and keeps launching Windows...

Im running Windows 8.1 OEM

What can I do?

By the way: I installed it using "Near Windows-Boot" so Linux should automatically create a partition for itself and install there...
I assigned it 50GB... In disc manager I can see 2 partitions (38,92GB and  7,82GB), however it says that theese partitions are empty (100% free)...

---

### Post by Vladlenin5000 on 2015-07-23
Hi and welcome.

If Windows 8.x is installed in UEFI mode as most preinstalled are, you must install Ubuntu the same way.

---

### Post by hultongetty on 2015-07-23
So I will need to install linux once again, huh?
So actually, ubuntu is not installed and all its files were deleted?

Any tutorials? I've installed it near Windows 7 and had no problems...

---

### Post by Vladlenin5000 on 2015-07-23
All factory installed Windows 7 came in BIOS mode, even the latest in UEFI hardware. Windows 8 and newer always in UEFI mode and sooner than later everything else will have to be.
Ubuntu runs fine either way but for dual boot purposes it needs to be installed in the same mode as the other OS. Otherwise you would have to go to BIOS/UEFI settings for each boot to enable/disable legacy (or CSM) mode as required and many do not make it easy.
How you boot the installation media is how it installs.
Start here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)[URL="https://help.ubuntu.com/community/UEFI"]
[/URL]

---

### Post by hultongetty on 2015-07-23
And if I won't install Ubuntu in UEFI, am I actually able to boot it by switching BIOS to Legacy Mode?

---

### Post by Vladlenin5000 on 2015-07-23
> **hultongetty said:**
> And if I won't install Ubuntu in UEFI, am I actually able to boot it by switching BIOS to Legacy Mode?

Good question. It varies. Only you can test yours.

---

### Post by hultongetty on 2015-07-23
Haha, too late... Deleted those empty(?) partitions...
I will try to install in UEFI mode... Hope it will work.

---

### Post by hultongetty on 2015-07-24
Great! Another problems!
This time I tried to lauch fresh installer from USB... Instead of loading/installation Ubuntu screen I saw a dark screen for over 10 minutes...
I canceled everything.  I have found my old iso with Ubuntu 13 burned on a DVD... The same situation. Dark, black screen. No loading, no installing...
What the hell is happening? 

Windows is really corrupting linux... When I had no OS everything went OK. Everytime when I try to do anything with linux while having Windows on HDD... Nothing works properly.

---

### Post by oldfred on 2015-07-24
Is Windows installed in UEFI or BIOS mode. You can install in either mode.
And if you did install Windows in UEFI, then BIOS, it does not correctly convert from gpt partitioning to MBR partitioning. Then Ubuntu installer cannot find any correct partitions, so assumes you want to erase entire drive. 
You can use fixparts to repair partitioning, but better to have both systems on a gpt partitioned drive booting in UEFI mode.

From Windows Linux partitions will always look empty.

You do have to have Windows fast startup off. Which is really just always on hibernation.
       Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Use Windows to shrink the NTFS partition and reboot immediately so it can run chkdsk and repair to its new size. 
The Linux NTFS driver will not mount NTFS partitions that are hibernated or need chkdsk. So then an installer cannot see Windows.

Lots more info in link below in my signature.

What brand/model system or motherboard? And what video card/chip?

---

### Post by hultongetty on 2015-07-24
Oh, fast startup off... 
Aye, I don't have free partition right now... So that's why it didn't run...
Mhm, Im not sure if I want to turn off fast startup... Its really useful and I use it few times everyday... but if it's needed...

Actually I don't need to install Ubuntu immediately. I'll give up installing it right now.
At least I know what to do later...
 Thanks!

---

### Post by hultongetty on 2015-07-24
Okey. So basically as before I have created NFS partition (around 50gb)... Its checked and empty.
But still - When Im trying to run linux install, it freezes and nothing happens...

This is (if I remember good Acer Aspire V3-571G. I have no idea about motherboard. Every checking soft says somenthing different).
GPU: Nvidia Geforce GT630M

---

### Post by hultongetty on 2015-07-24
Okey. Looks like its installed. On UEFI for sure.

But still - windows launches all the time and I cant boot ubuntu...
Any downloadable boot menager doesnt work...

---

### Post by oldfred on 2015-07-24
Acer requires you to also add a password in UEFI (never lose that) which then opens up more settings. And then you have to enable trust for the ubuntu entry and its boot files.

You may then also need nomodeset at grub menu on linux line to boot, until you install nVidia driver from Ubuntu repository.

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

All Acer models seem to have very similar UEFI settings:
      
 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[URL="http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot"]http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot
[/URL]
 Acer E3 requires UEFI password to allow added settings Post #8
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=2253311

[/URL]

---

### Post by hultongetty on 2015-07-24
Okey... But still - how to boot linux?!
I can't do it...
I have BIOS password set...

---

### Post by oldfred on 2015-07-24
Once you have set trust, you should have an entry in the UEFI boot tab. Or one time boot key if Acer has one, often f10 or f12.

---

### Post by hultongetty on 2015-07-24
Enable trust... Can't see any security/permissions enabling tab/switch.

---

### Post by oldfred on 2015-07-24
Did you read the first link I gave? This one:
[http://ubuntuforums.org/showthread.php?t=2256083&page=2&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&page=2&p=13203044#post13203044)

User explains more about what he had to do to enable trust.

---

