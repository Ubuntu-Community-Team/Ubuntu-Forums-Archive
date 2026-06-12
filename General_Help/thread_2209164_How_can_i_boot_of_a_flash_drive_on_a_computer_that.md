---
title: "How can i boot of a flash drive on a computer that is already a duel boot?"
date: 2014-03-04
forum: General Help
---

### Post by michael114 on 2014-03-04
my computer is already a duel boot machine (ubuntu (4Gb) and windows 7(the rest of 500 Gb's)) and when i plug in the flash drive (a ubuntu 13 bootable stick) i don't get the option for booting off of it, please help?!

i'm trying to increase the partition size of ubuntu btw.

---

### Post by varunendra on 2014-03-04
Welcome to the forums michael114 !

The number of installed OSes on the hard disk doesn't affect the booting of a Live media (CD/DVD/USB). You may not be able to install it in some cases, but you should always be able to boot a live DVD/USB.

How did you install the previous instance of Ubuntu?
How have you created the current Live USB?

---

### Post by jp734 on 2014-03-04
BIOS setup?

---

### Post by michael114 on 2014-03-04
i installed ubuntu through the WUBI.exe gotten from the ubuntu site, i have made the flash drive bootable using a tool um, it was some sort of tool that was in the directions on a makeusof.com article...

could it be that i have it plugged into a USB hub?

---

### Post by buzzingrobot on 2014-03-04
> **michael114 said:**
> 
could it be that i have it plugged into a USB hub?

I would certainly  attach the USB directly to the machine.

You are resetting the BIOS to boot off the USB or interrupting the boot to do the same?

---

### Post by michael114 on 2014-03-04
> **buzzingrobot said:**
> 

You are resetting the BIOS to boot off the USB or interrupting the boot to do the same?

could you go more into detail here? i don't understand.

---

### Post by sudodus on 2014-03-04
I don't want to disturb your dialogue, but if you are still having problems at the end of the current path, have a look at ***chainloading*** from the current grub menu to the USB pendrive according to this link

[https://help.ubuntu.com/community/Installation/FromUSBStick#Chainloading](https://help.ubuntu.com/community/Installation/FromUSBStick#Chainloading)

---

### Post by grahammechanical on 2014-03-04
On the motherboard there is an integrated circuit that holds some code that explains to the motherboard the devices that are connected to the motherboard. It is called Basic Input Output System (BIOS). It in the BIOS that the motherboard learns where to look for an operating system and in which order to search. It is usual for the motherboard to search first the hard disk. If it finds an OS there then it will load that OS. We need to change the BIOS setting to tell the motherboard to look first on a USB memory stick then on the hard disk. Or if we are using a Ubuntu install DVD disk to look to the optical drive before looking to the hard disk.

So, have you changed the settings in the BIOS? It is also possible that your machine has UEFI instead of BIOS but the principle is the same.

Regards.

---

### Post by Impavidus on 2014-03-04
> **michael114 said:**
> i installed ubuntu through the **WUBI.exe** gotten from the ubuntu site, i have made the flash drive bootable using a tool um, it was some sort of tool that was in the directions on a makeusof.com article...

could it be that i have it plugged into a USB hub?(emphasis mine)

wubi doesn't give you a real dual boot. It's Ubuntu on a virtual partition, stored in a file on the Windows partition. Wubi installs have to be resized in a different way. See here: [https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)

The limit is 30 GB. If you want something larger, you have to move on to a real dual boot. Real dual boots are somewhat better too and wubi is being phased out, but you may want to continue using your wubi install until 14.04LTS is released, moving on at a convenient time.

---

