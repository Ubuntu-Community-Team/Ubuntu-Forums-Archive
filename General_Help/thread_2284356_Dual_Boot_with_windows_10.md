---
title: "Dual Boot with windows 10"
date: 2015-06-29
forum: General Help
---

### Post by bobmac on 2015-06-29
Folks,

I am currently running windows 7 dual booted with ubuntu 12.04 LTS. I have registered to receive windows 10. 

Does anyone have any idea what, if any, effect on ubuntu 12.04 LTS will occur if I install windows 10?

Regards,

Bob

---

### Post by Bucky Ball on 2015-06-29
*Thread moved to **Ubuntu, Linux and OS Chat**.*

What effect do you mean? Will it effect the booting of Ubuntu? I would imagine yes. Will effect the actual Ubuntu install? No, unless you accidentally wipe Ubuntu in the process of installing Windows.

---

### Post by bobmac on 2015-06-29
Folks,

Do you have any idea in which way it will  effect the booting of Ubuntu? Although I've been using ubuntu for a while I'm no guru. I'm just an ordinary user trying to get away from windows.

Regards,

Bob

---

### Post by Bucky Ball on 2015-06-29
It depends on how you have Ubuntu installed as to how you go about it I'd think. Is Ubuntu installed in EFI mode or legacy? Have you already got four partitions on that drive if the latter? If the former, theoretically Win should simply add its entry to the EFI partition and will be well, but it is Windows, so doubt it's that simple. I could be pleasantly surprised ...

---

### Post by westie457 on 2015-06-29
Does this post answer your question. [http://ubuntuforums.org/showthread.php?t=2281155&p=13298351#post13298351](http://ubuntuforums.org/showthread.php?t=2281155&p=13298351#post13298351)

The above is for an installation with a regular BIOS .. AKA legacy.

For an installation with UEFI you will probably have to reset the boot order in the System Setup Settings.

---

### Post by bobmac on 2015-06-29
Bucky Bill,

I'm afraid I don't what EFI is or how it was installed. All I did to get ubuntu 12.04 was to download it from a mirror site (Internode), create a disk and use the disk to install it.

Also, I've got ubuntu installed on a second HDD. I don't know if that changes anything.

Using Gparted to display the ubuntu disk, I have:

/dev/sdb2 ext3 /(mount point) then the size etc.
/dev/sdb1 extended etc.
    /dev/sdb5 linux-swap etc.

reards,

Bob

---

### Post by Bucky Ball on 2015-06-29
> **westie457 said:**
> Does this post answer your question. [http://ubuntuforums.org/showthread.php?t=2281155&p=13298351#post13298351](http://ubuntuforums.org/showthread.php?t=2281155&p=13298351#post13298351)

So, in other words, you are going to boot to the BIOS and see if you are using EFI or legacy install for Ubuntu. Legacy is easy. Install as per normal, with a four partition limit. Don't know about dual-booting with EFI (although I installed Xubuntu on a machine the other day with Win8 and it just worked). Sounds like [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") will fix either, hopefully.

---

### Post by monkeybrain20122 on 2015-06-29
MS is forcing people to make these choices by making Windows extremely unfriendly to dual booting. Unless Windows is necessary I will just give it the boot.

If You are currently running Win7 chances are it is in BIOS mode. I am not sure if upgrading to Win10 would change that but to be sure just make sure UEFI is disabled before upgrading.

---

### Post by bobmac on 2015-06-29
Folks,

Thank you so much for putting up with my dumbness. I've copied everything to a file so hopefully I'll be ready when it all goes pear shaped (You never know, It might just work first time :-).

Many thanks again,

Regards,

Bob

PS I was going to set this post to solved but the drop down for thread tools has the solved option missing?

---

### Post by Bucky Ball on 2015-06-29
Try solved now.

If you have issues booting Ubuntu after you've installed Windows 10 post a new thread outlining specific issues and with a descriptive title. Thanks.

(Create a bootinfo summary with Boot Repair or using bootinfoscript and post it on the new thread.)

---

