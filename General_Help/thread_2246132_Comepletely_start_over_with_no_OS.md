---
title: "Comepletely start over with no OS"
date: 2014-09-28
forum: General Help
---

### Post by kushwin on 2014-09-28
i have the black screen and blinking cursor
 i want to know if i can fix it or
just restart my computer completely with no os

Intel® Core™ i5-2390T CPU @ 2.70GHz × 4 
Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits)
64-bit

---

### Post by AnotherKevin on 2014-09-28
Put your install disk in and turn your computer on.   It should take it from there. 
Kevin

---

### Post by kushwin on 2014-09-28
> **AnotherKevin said:**
> Put your install disk in and turn your computer on.   It should take it from there. 
Kevin

i did that 
already first thing i did
i installed it all over again 
but it just goes back to the black screen

---

### Post by Bashing-om on 2014-09-28
kushwin; Hi !

Try booting with the "nomodeset" boot parameter,
Reboot, soon as bios screen clears depress and hold the right -shift- key -> language screen, escape key to accept the default -> boot options screen ->
F6 key for boot options: use the space bar to page down, Tab to highlight , then Enter to accept.

Once you are installed, from the "Additional drivers" utility, select a graphics driver.

[INDENT][INDENT][INDENT]hope this works
[/INDENT][/INDENT][/INDENT]

---

### Post by kushwin on 2014-09-28
> **Bashing-om said:**
> kushwin; Hi !

Try booting with the "nomodeset" boot parameter,
Reboot, soon as bios screen clears depress and hold the right -shift- key -> language screen, escape key to accept the default -> boot options screen ->
F6 key for boot options: use the space bar to page down, Tab to highlight , then Enter to accept.

Once you are installed, from the "Additional drivers" utility, select a graphics driver.
[INDENT][INDENT][INDENT]hope this works
[/INDENT]
[/INDENT]
[/INDENT]


i tried that a while back
but it didnt work 
thanks anyways 
i just want to start all over like the first day it was built 
nothing on it

---

### Post by Bashing-om on 2014-09-28
kushwin; Hey;

Confused here as; IF you boot the liveDVD, and select "install" and in the install screen select "erase disk and install ubuntu" it does just that. Wipes the disk; installs ubuntu.

[INDENT][INDENT]where can the problem lie is such a simple thing ?[/INDENT][/INDENT]

---

### Post by kushwin on 2014-10-01
i did that but
it still comes with a black screen 
with a blinking cursor

---

### Post by CraigPid on 2014-10-01
Does the black screen with blinking cursor come up after the grub screen or do you get no grub screen at all? Maybe you didn't install grub or you installed it in the wrong partition.

---

### Post by CraigPid on 2014-10-01
Try this
[http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)

---

### Post by grahammechanical on 2014-10-01
> [COLOR=#000000]ust restart my computer completely with no os[/COLOR]

That is easy to do. Load a Ubuntu live session and at the desktop load Gparted and delete the partition table. That should "fix" that hard disk good and proper. You could also use the Disks utility to format the drive. That will do what you want, as well.

But may I suggest something else? Ubuntu is trying to load to a desktop using a fallback video open source driver. That is what Gallium llvmpipe is used for in Ubuntu. It suggests to me that the problem is to do with the proprietary video drivers. And I wonder if you have hybrid graphics.

Anyway, the live session does not use a proprietary video driver. It uses an open source video driver. So, if the live session loads to a desktop, then I suggest that you install Ubuntu but this time do not tick the box "install third party software." Then you will not automatically get a proprietary video driver and you may get a working desktop. Then you can mess around with proprietary video drivers.

Blanking the hard drive is not going to change the hardware specification of the machine. What graphic adapters do you have?

Regards.

---

### Post by oldfred on 2014-10-01
The nomodeset works if you have AMD or nVidia, but if you are using the Intel video you may need other boot parameters. See other boot options by ubfan1, most are for Intel. Some systems also require UEFI/BIOS settings or other boot parameters in addition.

If only Ubuntu you need to hold shift key if install is BIOS or use escape key if UEFI.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

If none of that works then run Boot-Repair which is CraigPID's suggestion above.

---

### Post by kushwin on 2014-10-01
> **CraigPid said:**
> Does the black screen with blinking cursor come up after the grub screen or do you get no grub screen at all? Maybe you didn't install grub or you installed it in the wrong partition.

i forgot about that until after 
i dont think i ever installed it

---

