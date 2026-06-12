---
title: "XP in VirtualBox"
date: 2007-08-31
forum: General Help
---

### Post by trim17 on 2007-08-31
I had an old ThinkPad that died  on me a few years ago. For some reason the power supply pooped out, but I put the hard drive into an external 2.5" enclosure and left all the data intact (including the operating system, XP). 

I just made the switch over to Ubuntu (64-bit Feisty Fawn) and I'm happy to have done so. However, I'm curious about the feasibility of an interesting feat.

I installed VirtualBox, and I created a Virtual Machine that I want to install XP to. Is it possible, instead of using a CD to install to this new virtual machine, to clone the external drive to the virtual hard drive? It seems to me that this would work, using dd, but I just don't know how to copy a disk image to a virtual drive without an OS on the virtual machine.

Any solutions are greatly appreciated, and thanks for keeping the Ubuntu community the most friendly and helpful there is!

---

### Post by wolfen69 on 2007-08-31
i saw a workaround for this on the web somewhere, but it looked VERY involved and a lengthy process. plus there would be no guarantee this would well anyway. i think you are better off installing xp in VB the regular way. maybe someone here knows more about this than i do. good luck.

---

### Post by trim17 on 2007-08-31
Thanks for the reply. I'm not too afraid of long workarounds, though easy simple solutions are always preferable, so I might try the CD. The other reason I would like to use the external drive is that I had a copy of Microsoft Office 2003 and other things on it that I would like to have without having to buy or track down the CDs.

Some other things that might be important but maybe weren't clear earlier: 
I have a SATA drive as my boot disk for my computer.
The external hard drive (the one I want to use as the virtual drive) connects through USB
There aren't any partitions on the external hard drive.
I believe the filesystem on the drive is fat32.

Thanks again for the help!

---

### Post by oliverb4ss on 2007-08-31
I would make an image of the external harddrive and then point that image to VirtualBox for it to use it as the medium from which to boot the virtual XP.

VirtualBox requires the image to be a .vdi-file (or something like that, I might be wrong about that extension), so you'll have to convert the image into that filetype. But how to do that, I'm not sure.

Well, I hope I've pushed you in the right direction.

---

### Post by trim17 on 2007-08-31
Well, I was thinking of this, but I mentally ran into the same problem as you: I don't know how to *dd* the external drive to a format that could be used by Virtualbox as a drive. I know I'll be using dd to copy the hard drive to an image file; I don't know how to do that without possibly borking either drive :(. Thanks for the help.

---

### Post by bodhi.zazen on 2007-08-31
Well, booting a physical partition like you are asking is possible, but it is in alpha testing at this time.

The problem is the "hardware" changes in that VirtualBox (and VMWare) work by creating a virtual set of hardware.

See these links for a start :

Boot windows partition :

		[http://www.virtualbox.org/download/UserManual.pdf](http://www.virtualbox.org/download/UserManual.pdf)
			See section 9.8.2 Access to individual physical hard disk partitions

		[http://oopsilon.com/Running-a-Windows-Partition-in-VMware](http://oopsilon.com/Running-a-Windows-Partition-in-VMware)

		Then [http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

And, of course, there is no guarantee it will work. If you search there is a thread on these forums here from a user trying (unsuccessfully) to do this.

---

### Post by trim17 on 2007-08-31
Whoa. Lots and lots of work involved here. 

It's all been very helpful, though. It's looking like this might pose a problem:

> Hard Disk Support 

For reasons we don't understand, Windows memorizes which IDE/ATA controller it was installed on and fails to boot in case the controller changes. This is very annoying because you will run into this problem with basically all migrated images. The solution here is to perform several modifications to the Windows registry. This can be done while the installation is still running on the original system because all it does is relax the IDE checks. ... [snip]

[virtualbox.org/wiki/Migrate_Windows]

I'm gonna try this anyways; I've got some time to see if I can make this work.

---

