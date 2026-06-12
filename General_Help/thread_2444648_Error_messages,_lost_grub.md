---
title: "Error messages, lost grub"
date: 2020-06-02
forum: General Help
---

### Post by 0doubled7 on 2020-06-02
Hi folks not sure if this would be considered an Install or General, or lol all of the above. 
The problem initially started with an upgraded GTX 1660 graphics card and driver issues in Ubuntu 18 and evolved into the following mess.
I was dual booting with Ubuntu and win7 pro. I had problems with the Ubuntu install. I was upgrading to ver 20. I was going to delete the partition where I assumed Ubuntu was installed. I ended up not being able to boot into windows. 
I formatted the partition and reinstalled Windows.  I would like to get a path back to windows and also install Ubuntu ver20. 
I have tried the Windows install disk and selected "Repair System" multiple times. I have tried the "Command Prompt as "Administrator" and tried the bootrec /fixmbr, bootrec /fixboot, bootrec /rebuildbcd.
I ran bootrec /scanOS and got the following:
Successfully scanned windows installations. 
Total identified installations: 0
This operation completed successfully
I can boot into Windows using Grub and the Windows Install disk. When I boot without the install or Grub, I get this message:
'/boot/grub/i386-pc/normal/.mod.
I have also gotten this message: 0xc00000e9  and this message:
root>\sys32\hal.dll.
I have attached/uploaded a copy of my bcdedit but don't see it so I will post a copy below:


Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.


C:\Windows\system32>bcdedit

Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=\Device\HarddiskVolume1
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {current}
resumeobject            {b7029ae0-7148-11e1-bc2a-dc4489b1c4d9}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 30

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows 7
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {b7029ae2-7148-11e1-bc2a-dc4489b1c4d9}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {b7029ae0-7148-11e1-bc2a-dc4489b1c4d9}
nx                      OptIn

C:\Windows\system32>

Thanks for the help

---

### Post by CelticWarrior on 2020-06-02
Welcome.

Windows 7 is something you and everybody else SHOULDN'T be using. It is and has been out of support for a very long time.
Also this isn't a Windows support forum. Dual-booting is often discussed here but there are better places to get help for installing Windows alone.
If you want to dual-boot in BIOS mode then install Windows first, Ubuntu second. If using UEFI mode the order isn't relevant.

---

### Post by 0doubled7 on 2020-06-02
Thanks for the info. If I install Ubuntu again, will it recognize my windows installation and provide a grub, even though my system doesn't recognize it?

---

### Post by CelticWarrior on 2020-06-02
Ubuntu uses Grub as the bootloader. Grub can also boot (chainload to the Windows bootloader) any working working. If the installed Windows doesn't boot, Grub won't boot it either. Please explain what you mean by "my system doesn't recognize it".

---

### Post by 0doubled7 on 2020-06-02
When I try to boot up the screen comes up to Grub Rescue, I then have to stick the Windows Installation DVD in or use my Grub Boot Boot (Rescue Disk) to boot into Windows.

---

### Post by 0doubled7 on 2020-06-02
I can also use Hirens Boot CD to get to Windows Login.

---

### Post by CelticWarrior on 2020-06-02
That happens because you have a BIOS mode installation -and- you deleted the Ubuntu system partition where the every stage of the initial Grub boot except the first happens. In such situations reinstalling Ubuntu should be enough but if you want to keep Windows only you must boot a Windows installation media to reinstall the Windows bootloader. This does not happen with modern, UEFI mode, installations.

---

### Post by 0doubled7 on 2020-06-02
Yes I want both Windows and Ubuntu with the option to dual boot. So, you are saying that if I reinstall Ubuntu, that it will create a grub for a dual boot?

---

### Post by CelticWarrior on 2020-06-03
Yes, that is what I'm saying.

---

### Post by 0doubled7 on 2020-06-03
Ok update. Bought a key for Win 10 and installed using the upgrade option. Result,  unable to get into Win10 from the boot. So, I loaded and installed Ubuntu 20, It didn't produce a Grub screen. Now working on same problem trying to boot into Windows without the assistance of the Grub and or Hiren's Boot CD. I did burn an ISO of Win 10 on a flash drive as I was going to do a fresh install, but my BIOS was having none of that. So now, not sure what I need very little experience with Win10.

---

### Post by CelticWarrior on 2020-06-03
Again, if Windows doesn't boot by itself, Grub won't boot it either.
If it's a new UEFI system (that mean its firmware is not BIOS but UEFI), regardless of the mode Windows 7 was installed before (BIOS/Legacy mode) you can now and should install Windows and Ubuntu in UEFI mode. That has the huge advantages: 
[LIST=1]
[*]allowing co-existence of bootloaders so you can entirely delete one OS' partitions and always be able to boot the other;
[*]major Windows system updates (feature updates) no longer remove Grub
[*]Windows no longer messes with the partition table (because GPT).
[/LIST]

So, the first thing to check is whether or not your hardware supports UEFI. If not, i.e., being BIOS, nothing of the above applies and you'll have to install the dual-boot as before.
With BIOS/Legacy always install Windows first and for any Windows 8+ in BIOS or UEFI always disable Fast Startup before installing the second OS, Ubuntu.

Please post your hardware specifications.

---

### Post by 0doubled7 on 2020-06-03
Gigabyte Z68X-UD3H-B3 rev 1.3  LGA 1155 socket 2
Intel I-5 2500k processor
 Corsair 16Gb
Nvidia GTX 1660 Super OC Graphics card  -newly installed

BIOS    
2 x 32 Mbit flash
Use of licensed AWARD BIOS
Support for DualBIOS&#8482;
PnP 1.0a, DMI 2.0, SM BIOS 2.4, ACPI 1.0b




[LIST=1]
[*]2 x 32 Mbit flash
[*]Use of licensed AWARD BIOS
[*]Support for DualBIOS&#8482;
[*]PnP 1.0a, DMI 2.0, SM BIOS 2.4, ACPI 1.0b
[/LIST]

---

### Post by CelticWarrior on 2020-06-04
New enough to have UEFI (the vendor still refers to it as "BIOS" but it isn't).
So, as above, install both in UEFI mode. For that prepare the drive before installing any of them. Make sure you have all the backups you need because the following operation will erase all data.

Boot a Ubuntu live session, open Gparted and make sure the drive in question is selected. Go to Devices menu > creat partition table and select GPT type. Again, this will erase all data.

Then open UEFI ("BIOS") settings and look for UEFI boot related settings and/or CSM. You want to enable the former only, instead of "UEFI+Legacy" and disable the former. Also disable Secure Boot and Fast Boot. DFone that and you have everything you need to assure both installation media will boot and install in UEFI mode: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

