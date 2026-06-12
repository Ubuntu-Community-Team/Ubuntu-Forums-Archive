---
title: "Unable to boot my system"
date: 2014-11-09
forum: General Help
---

### Post by Kottizen on 2014-11-09
After I installed Kubuntu 14.10 a couple of weeks ago, I have been unable to boot my Windows, on the same PC. It was not a problem until yesterday, when I unfortunately needed to access Windows in order to run a Windows-only application. By a fellow in #ubuntu, I was introduced to Boot-Repair-Disk, a live CD that could fix common boot issues.

I ran Boot-Repair-Disk, chose "Recommended repair", and ended up with not being able to boot any of the two installed operating 

Just like last time, I get this message when I first run Boot-Repair-Disk. As I have no other option, I press OK and the application seems to be starting.
"Warning: this will install necessary packages from Ubuntu-13.04 repositories. Please backup your data before this operation."

If I press Recommended repair, I am notified of this:
"The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode. Do you want to continue?"

First, I chose No, went to the Advanced options of Boot Repair, to look for this EFI mode. Being unable to find it, I ran the Recommended repair again, this time choosing Yes on the above question.

Boot Repair now went through a couple of steps, and somewhere in the middle I was asked to enter first three commands, followed by a fourth command. This is the output from those commands:
[http://martin.pola.org/paste1.txt](http://martin.pola.org/paste1.txt)

After having executed the last command, I got a message saying "GRUB is still absent. Please try again." I tried five times before pressing Discard, which led me to this message:
"GRUB reinstallation has been cancelled. sdb1 is now without GRUB."

And that's it! Now I can't boot anything.


Here is the output from Boot Repair's "Create a BootInfo summary":
[http://martin.pola.org/paste2.txt](http://martin.pola.org/paste2.txt)


My Windows is on an HDD and my Kubuntu is on an SSD. I would like to be able to boot any of them. What should I do?

---

### Post by yancek on 2014-11-09
How old/new is this computer?  Do you have an option for UEFI/GPT partitioning in the BIOS?  Your problems include having the syslinux bootloader in the master boot record of sda, your windows hard drive and also having an EFI partition on that drive (sda2).  You have both windows and Ubuntu EFI files in the partition.  The message below shows in the output you posted, did you do this?

> The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode

and just below that in the output it shows:

> Please do not forget to make your BIOS boot on sda2/efi/.../grub*.efi file!

You selected not to make any changes.  Since you have the EFI files set, you might try setting your BIOS to UEFI.  I don't use it so if that doesn't help, someone else more familiar with it should be along to help.

---

### Post by Kottizen on 2014-11-09
I think I have now successfully gone from Legacy to UEFI. I am, however, not sure how do make my "BIOS boot on sda2/efi/.../grub*.efi". How would I do that?

Here are two pictures showing the Boot section of my BIOS:
[http://martin.pola.org/IMAG6116.jpg](http://martin.pola.org/IMAG6116.jpg)
[http://martin.pola.org/IMAG6117.jpg](http://martin.pola.org/IMAG6117.jpg)

If I enter the CSM section, this is what I see:
[http://martin.pola.org/IMAG6118.jpg](http://martin.pola.org/IMAG6118.jpg)

And regardless of which of the three devices I choose in the Boot Override list, I always get this:
[http://martin.pola.org/IMAG6114.jpg](http://martin.pola.org/IMAG6114.jpg)

---

### Post by Sef on 2014-11-09
seems as if you highlight boot order 2, you could move it up.

---

### Post by oldfred on 2014-11-09
Normal not found is usually trying to boot in wrong mode. Or you installed in UEFI and are booting in BIOS or vice-versa.

I have an Asus-AR motherboard and had to turn off Windows boot mode(which really was only secure boot) and had to turn on UEFI only in CSM which also seemed strange. I would think UEFI & CSM should be two separate settings.

---

