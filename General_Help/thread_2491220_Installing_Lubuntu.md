---
title: "Installing Lubuntu"
date: 2023-09-30
forum: General Help
---

### Post by daniell59 on 2023-09-30
I would like to install Lubuntu on an old computer. The computer won't boot from a USB flash drive. There is no DVD drive. Is there a way of doing this from the HD?

Danny

---

### Post by guiverc on 2023-09-30
You've provided no hardware details, including no architecture.

I've used old laptops for QA testing (*Quality** Assurance*) that didn't have working USB ports, by copying the ISO to one partition on the machine, then running a script to make the existing boot loader of the computer system offer options to boot the ISOs in a directory. If I performed install tests, they'd be done to other partition(s) of the disk. One of those devices (*with no working bootable USB ports)* did have a DVD drive, but I opted to not use that, as the idea of writing a DVD each day for a test didn't appeal to me.

So yes this is possible, but it's far more work than using a USB flash drive, or DVD media. If I was installing a system only once, I'd likely have used DVD or *optical* media myself, but in QA testing the procedure is repeated up to *daily*.  How you modify the boot loader will depend on what OS & boot loader is currently being used. In my own case, my boot loader was GRUB (*it wasn't actually a Ubuntu system, but that didn't matter, I was using Ubuntu including Lubuntu ISOs in my QA*).  I've also done it *long ago* (decade+) by having a windows boot loader chain to a Linux system (*but I'd not want to do that again** as it was a pain*).

If the machine won't boot from USB drive, why?  Booting from USB ports was introduced end of the 1990s though wasn't common until around 2005. Issues vary on why a machine won't boot, some hardware even as late as 2010 would only boot a USB drive if a single USB port was connected (ie. machine *firmware* had no capacity to select which drive to boot, so to boot only one port could be used; though usually this wasn't impacted by mouse or keyboards using USB; only USB storage devices mattered)

---

### Post by daniell59 on 2023-09-30
MB Biostar MCP6P M2+/N68S
CPU AMD Athlon 64 X 2 dual core

---

### Post by Rex Bouwense on 2023-09-30
Some of the older computers did indeed have no capability to boot from a USB flash drive in the BIOS.  However, I did discover that they more than likely considered an inserted  flash drive as a second hard drive.  Yours may be one of those so check the BIOS to see if the boot order under hard drive discovers your flash drive.  If it does simple move it ahead of your spinning hard drive and attempt to boot.

---

### Post by daniell59 on 2023-09-30
> **Rex Bouwense said:**
> Some of the older computers did indeed have no capability to boot from a USB flash drive in the BIOS.  However, I did discover that they more than likely considered an inserted  flash drive as a second hard drive.  Yours may be one of those so check the BIOS to see if the boot order under hard drive discovers your flash drive.  If it does simple move it ahead of your spinning hard drive and attempt to boot.

When I insert the flash drive, the computer freezes at the point where it asks what do I want to boot from.

---

### Post by sudodus on 2023-09-30
It might work to use **Plop**, to boot to a floppy disk or CD, and let Plop supply a driver that makes it possible to chainload to the USB drive. See [this link](https://help.ubuntu.com/community/Installation/FromUSBStick/bootUSB#PLoP_Boot_Manager)

[hr][/hr]
Edit:

- What operating system is there on the target computer now (name, version)? Is it working?

- Would you like to install Lubuntu onto the whole drive or make a dual boot system with Lubuntu alongside the current operating system?

- Have you got some other computer, where you can prepare the boot media?

- Would it be an option to move the internal hard disk drive from the target computer and connect it to another computer as an external or internal drive?

---

### Post by daniell59 on 2023-09-30
> **sudodus said:**
> It might work to use **Plop**, to boot to a floppy disk or CD, and let Plop supply a driver that makes it possible to chainload to the USB drive. See [this link](https://help.ubuntu.com/community/Installation/FromUSBStick/bootUSB#PLoP_Boot_Manager)

[hr][/hr]
Edit:

- What operating system is there on the target computer now (name, version)? Is it working?

- Would you like to install Lubuntu onto the whole drive or make a dual boot system with Lubuntu alongside the current operating system?

- Have you got some other computer, where you can prepare the boot media?

- Would it be an option to move the internal hard disk drive from the target computer and connect it to another computer as an external or internal drive?

I was just trying to determine why I could not boot from the flash drive. I don't depend on the computer. The computer that I depend on is at least 15 years old. It allows me to boot from the USB. Soon I will build another computer. I am deciding between AM4 or AM5.

---

### Post by sudodus on 2023-09-30
If it works, the simple solution is via Plop.

An alternative is to move the internal hard disk drive from the target computer and connect it to the other computer, either internally or via a USB to SATA (and/or) IDE adapter.

Then you can simply extract and clone from a compressed image of Ubuntu Server, move it back to the target computer, boot it and then install lubuntu-desktop and make it Lubuntu. See [this link](https://ubuntuforums.org/showthread.php?t=2474692). Read the whole thread before starting the installation. I would suggest installing the version Jammy (22.04.x LTS).

---

### Post by ne29914 on 2023-09-30
I have the same problem, also on 15+ years old laptops.
The trouble started somewhere between Lubuntu 20.04.1 and 20.04.5.
20.04.1 will boot fine from a USB thumb drive, 20.04.5 and later will not. OTOH, 20.04.5 and later will boot fine from a DVD. That won't help you, I know.
You might go into the Lubuntu archives and find a 20.04.1 image and use that.
Yes, you'll have a real update party subsequently to get up to speed, but at least you'll have a working system.

Cheers.

---

### Post by sudodus on 2023-09-30
@ne29914,

When the problem is like yours, the method you describe is good.

It is more complicated to upgrade between releases, in this case from 20.04.1 to the current up to date 20.04.x and then to 22.04.x.

I would also try another method, to use [mkusb](https://help.ubuntu.com/community/mkusb) and the **[FONT=Courier New][SIZE=3]dus-iso2usb[/SIZE][/FONT]** method and select the 'settings'

- msdos partition table
- grold (old version of grub)
- bflag (boot-flag)

The boot system of some old computers can manage a USB drive with these features.

---

### Post by daniell59 on 2023-10-02
Let me preface this by saying that this is a learning opportunity more than a practical consideration.
I emailed Biostar. They responded in a very considerate manner. Though the board has not been supported for more than 10 years, they gave me some suggestions.

They told me that the Flash drive should be in FAT format. How can that be with a Linux ISO?

---

### Post by ne29914 on 2023-10-02
Been through all that as well. Biostar fobbed you off.

---

### Post by ne29914 on 2023-10-02
BTW, I see no mention in the thread about you setting up the BIOS for boot. Did you do this?

---

### Post by sudodus on 2023-10-02
> **daniell59 said:**
> Let me preface this by saying that this is a learning opportunity more than a practical consideration.
I emailed Biostar. They responded in a very considerate manner. Though the board has not been supported for more than 10 years, they gave me some suggestions.

They told me that the Flash drive should be in FAT format. How can that be with a Linux ISO?

You can try with [Unetbootin](https://unetbootin.github.io/) in Ubuntu or with [Rufus](https://rufus.ie/) in Windows.

---

### Post by daniell59 on 2023-10-03
> **ne29914 said:**
> BTW, I see no mention in the thread about you setting up the BIOS for boot. Did you do this?
Whenever I would insert the flash drive the computer would freeze. The BIOS only listed hard drives, floppy and CD and CDROM. In the case of my other computer, I insert the flash drive, go to BIOS and save it as the first device to boot. This indicates that the flash drive is functioning.

---

### Post by sudodus on 2023-10-03
> **sudodus said:**
> If it works, the simple solution is via Plop.

An alternative is to move the internal hard disk drive from the target computer and connect it to the other computer, either internally or via a USB to SATA (and/or) IDE adapter.

Then you can simply extract and clone from a compressed image of Ubuntu Server, move it back to the target computer, boot it and then install lubuntu-desktop and make it Lubuntu. See [this link](https://ubuntuforums.org/showthread.php?t=2474692). Read the whole thread before starting the installation. I would suggest installing the version Jammy (22.04.x LTS).

> **daniell59 said:**
> Whenever I would insert the flash drive the computer would freeze. The BIOS only listed hard drives, floppy and CD and CDROM. In the case of my other computer, I insert the flash drive, go to BIOS and save it as the first device to boot. This indicates that the flash drive is functioning.

In this case it seems that the USB system is seriously damaged and I suggest again, that you try the alternative to move the internal hard disk drive from the target computer and connect it to the other computer as described in a previous reply from me.

---

### Post by daniell59 on 2023-10-05
I reinstalled the Lubuntu iso using Rufus this time. The computer no longer freezes and I am now able to install it into the HD. My question is, why was the other computer not having those issues?

---

### Post by sudodus on 2023-10-05
Congratulations :-)

In order to analyze your previous problem, you must explain how you created the USB boot drive (when it failed, that is before using Rufus): The tool, the method, and if you did something to the computer (BIOS-UEFI system, etc.) Generally, some computers are easy-going, and some computers are tricky to boot. Usually it depends on the brand, version and settings of the BIOS-UEFI system.

---

### Post by daniell59 on 2023-10-05
Initially I created the the iso by using Start Up Disc Creator in Ubuntu.

---

### Post by sudodus on 2023-10-05
The Ubuntu Start Up Disc Creator clones from the iso file to the USB pendrive. This means that there will be an iso9660 file system and a hybrid boot system (that works both from DVD and USB (and SATA).

Rufus creates a partition with a FAT32 file system and extracts the content of the iso file to the FAT32 file system and fixes a grub boot system.

Your problematic computer is willing to boot from grub and the FAT32 file system, but not from the hybrid boot system.

---

### Post by daniell59 on 2023-10-05
> **sudodus said:**
> The Ubuntu Start Up Disc Creator clones from the iso file to the USB pendrive. This means that there will be an iso9660 file system and a hybrid boot system (that works both from DVD and USB (and SATA).

Rufus creates a partition with a FAT32 file system and extracts the content of the iso file to the FAT32 file system and fixes a grub boot system.

Your problematic computer is willing to boot from grub and the FAT32 file system, but not from the hybrid boot system.

Thanks

---

