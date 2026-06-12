---
title: "Need to install Windows 7 from HDD partition"
date: 2013-01-09
forum: General Help
---

### Post by Leopardson on 2013-01-09
Hi,

I've got an incredibly frustrating problem that has been swallowing my free time for three days now.

I need to install Windows 7. I have a USB stick that doesn't work and a DVD-RW.

Whenever I try to burn any Windows 7 iso using any DVD burning hardware using any burning software (Mainly XFBurn), and try to install them on any hard drive, the install fails at "Expanding files" and gives an error code 0x08070017.  I have tried literally every permutation of the above - everything from slowing down the DVD speed to using a different burner to switching between IDE mode and AHCI in the BIOS. I've gone through probably hundreds of threads discussing the issues I'm having and none of the solutions have helped.

I am using a Gigabyte GA-970-DS3, which uses the Award Bios that will not let me boot from a USB. I've tried all kinds of tricks and tips to get the BIOS to boot from the USB drive and it just won't. I updated my Bios version from F1 to F6 and now nothing detects the USB drive at all.

So I'm left with two hard drives - A 160gb 5-year old SATA which is where I have Ubuntu installed, and a completely empty 1TB WD10EZEX -  and a windows 7 ISO. I need to somehow create a bootable partition on one hard drive and use it to install windows 7 on the other hard drive. I don't care which hard drive gets the windows install, as long as I get one. 
 
After viewing many threads on things like this, I feel it is necessary to state this :
I do not have access to any sort of windows install whatsoever on any hard drive ever, and cannot use the Windows-only tools to do this. I have to do it from within Ubuntu.

How can I do this partition boot from Ubuntu? 
Do you guys have any other ideas that could get the install? 

Thanks!

[B]Edit: Using the Plop boot dvd that Cheesemill suggested, I was able to boot from the hard drive partition without having to do anything special - no USB drive was involved.
[/B]
Retrace of my steps in case anyone ever encounters this situation: How to install windows from a partition on one drive to another hard drive (Not tested with another partition on the same drive, but it might work for that too).

1. Used Gparted to make a 4gb partition on source hard drive.
2. Formatted partition to NTFS. Extracted contents of arbitrary windows 7 install ISO to the new partition.
3. Created Plop boot DVD, booted from it.
4. Plop detected the hard drive partition as HD0 Partition, selected it, and it surprisingly booted the install on the source drive and installed windows to the target drive with no errors of any sort - and it did it quickly, too.
5. Used Ubuntu live CD to fix MBR and restore GRUB.

---

### Post by mlentink on 2013-01-09
Don't you have friends with Windows boxes that can burn the iso for you? I can understand the inability to use usb, but not being able to burn a valid iso? 

As a wild guess, what you could also try to do is set up a virtual W7. Virtualbox can use iso to boot. If I recall correctly there are ways to convert a real life windows install to a virtual one, perhaps the opposite is also possible?

---

### Post by Cheesemill on 2013-01-09
I'd use [WinUSB]("http://www.webupd8.org/2012/01/tool-to-create-windows-usb-install.html") to create a bootable Windows 7 USB stick and then use a [Plop]("http://www.plop.at/en/bootmanagers.html") CD to enable your computer to boot from it.

---

### Post by Leopardson on 2013-01-09
> **Cheesemill said:**
> I'd use [WinUSB]("http://www.webupd8.org/2012/01/tool-to-create-windows-usb-install.html") to create a bootable Windows 7 USB stick and then use a [Plop]("http://www.plop.at/en/bootmanagers.html") CD to enable your computer to boot from it.

This is *exactly* the kind of reply I was hoping for. I'll definitely try this. Thanks!

---

### Post by Cheesemill on 2013-01-09
Let us know how it goes.

If that doesn't work then you *can* create a bootable partition containing the installation files on your blank drive, it's just a bit more involved.

Either way make sure you have a Ubuntu live CD handy as you'll need to reinstall grub after installing Windows.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Leopardson on 2013-01-10
> **Cheesemill said:**
> Let us know how it goes.

If that doesn't work then you *can* create a bootable partition containing the installation files on your blank drive, it's just a bit more involved.

Either way make sure you have a Ubuntu live CD handy as you'll need to reinstall grub after installing Windows.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

So when I was trying to make a boot partition myself, I just formatted a small 4gb partition and dumped the ISO files to it. When I booted with Plop, it couldn't detect my USB drive either, and I found out my USB drive died somehow. However, Plop was able to boot from the ntfs hard drive partition without any special formatting or changes, and it installed flawlessly!

I wish I had known about Plop earlier. It's definitely going in my hardware toolbox. 

Thanks again.

---

