---
title: "Combining Ubuntu and Win7 onto ONE DRIVE?"
date: 2016-03-02
forum: General Help
---

### Post by Biltron on 2016-03-02
My current setup is:  I have a 32GB drive with Ubuntu installed on it, the system boots from this disk, giving a GRUB selection menu.  If I select windows, it then boots off of my 480GB SSD that has Win7 installed on it.  

HERE is the million dollar question.

Is there a way to copy the linux partitions over to the 480GB drive, and somehow keep the linux partition the one that boots and gives the GRUB menu?

I want my dual-boot setup to function the same as it does now, but with everything on a single drive (the larger, faster, 480GB SATA3 SSD)

Is this possible?  If so, is it easy, medium, hard, or devil's work?

I know dual-boot can be done on a single drive, but I'm not exactly how to go from dual-boot dual-drive to dual-boot single-drive

You would think I would know how to do this, but apparently the computer engineering curriculum does not include partitioning (at least not the core classes :P )

fellow tech ppl, I respectfully request your recommendation, advice, and reply!

Thanks for reading
And remember not to put while loops in interrupt service routines ;)

Cheers,
BilTron

---

### Post by grahammechanical on 2016-03-02
You should read up on Globally Unique Identifier (GUID), Linux uses them. Every partition is assigned a GUID string which is a combination of alpha-numeric characters.

[https://en.wikipedia.org/wiki/Globally_unique_identifier](https://en.wikipedia.org/wiki/Globally_unique_identifier)

Grub uses the GUID to know where to look for the OS that we tell it to load. The new partition that you create for Ubuntu will have a different GUID to that listed in the grub.cfg. Even if you leave Grub installed in the MBR of the 32 GB drive it will still look to /boot/grub/ on the 32 bit drive for grub.cfg and it will not find it.

If you want to try this as an educational exercise, then go ahead. Me? I would install Ubuntu on the 480 GB drive letting the installer put Grub into the MBR of the 480 GB drive. That is the easiest way to do it.

Regards.

---

### Post by kurt18947 on 2016-03-02
I'm not really a technical person but do have Windows & Ubuntu booting off the same drive. If your machine came with Windows 7, it likely uses the old style BIOS and installing Ubuntu beside Windows is pretty straigtforward. If your machine came with Windows 8 or 10, it almost certainly has a UEFI BIOS. From reading here, it looks like UEFI experience varies by manufacturer and perhaps model. Some are as straightforward as the old style BIOS, others are a real challenge. Some HP models seem to be problem children. Other advice is to use Windows disk tools to move or shrink Windows partitions to make room. Gparted will resize NTFS partitions but may not do so to Windows' satisfaction. I don't blame you for wanting to have both OSs on your SSD. I have one in a laptop, thing goes like a bat :smile:.

---

### Post by yancek on 2016-03-02
> Is there a way to copy the linux partitions over to the 480GB drive, and  somehow keep the linux partition the one that boots and gives the GRUB  menu?


I'm not really sure what your actual goal is but this can be done.  The simplest thing to do is to leave the Ubuntu install where it is and continue booting from it and create Linux partitions on the larger drives to use for data.  If you want to move the entire install, that is possible but involves reinstalling Grub, updating Grub, changing UUIDs, etc.  A new install to the larger hard drive would be a lot simpler and faster but of course you wouldn't save your configurations from the old install.

---

### Post by gdesilva on 2016-03-03
One solution could be to do a partition image of the Ubuntu installation using Clonezilla. Then shrink Windows to allow space for the Ubuntu partition and using gparted create ext4 file system (equal or larger than the Ubuntu partition) and restore the saved Ubuntu partition on to the newly created ext4 partition on your ssd. Once this is done you will need to remove the disk containing Ubuntu and then reinstall grub so that it will pick up Win7 and Ubuntu OSs.

As grahammechanical says, it is so much easier to do a fresh install on the SSD drive and if you really need the data, copy them across to the new installation.

---

