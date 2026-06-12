---
title: "Re installing GRUB if dual booting another Linux distro (Gentoo)?"
date: 2013-03-01
forum: General Help
---

### Post by DeanM1134 on 2013-03-01
So today i'm going to be attempting to install Gentoo linux, partially for fun but also because I'm interested in the customization of the OS and the fact that it isn't Debian or Debian based, so it'll be a new experience. I'm confident in my ability to do so and follow the instructions, use the terminal, etc but my question is that because I've already got Zorin 6.1, and thus GRUB, installed on the hard drive I want to put it on, do I have to re install GRUB during the Gentoo install? It's included in the instructions (as usual) but I don't think they account for a dual boot or a separate GRUB installation. Shouldn't I just be able to install the OS and, assuming I do it correctly, boot my computer and have the old GRUB install detect it? It detects Windows 7 on a second internal HDD I have, and that still has the windows boot loader attached to it (I'm thoroughly impressed by this as I didn't think it would work like that, having never installed GRUB to that hard drive because it's purely Windows).

I've never been great with trying to dual boot things, in the sense that 90% of the time I screw up GRUB, especially when trying to dual boot two linux distros. But do I even have to bother?

---

### Post by grahammechanical on 2013-03-01
I have no experience with Gentoo but I would be very surprised if Gentoo did not want to install a bootloader of some kind and want to install it in the MBR of the disk it is being installed on. You may find during the partitioning section that you get options of where to install the bootloader. Ubuntu installs give us this option. If Gentoo installs its own bootloader into the MBR all you have to do is boot into Ubuntu (this is after all a Ubuntu forum and not a Zorin forum) and run these two commands

```
sudo update-grub
```

```
sudo grub-install /dev/sda
```

The first command tells Grub in Ubuntu to update and detect other OS and the second command writes Grub into the MBR of sda thus overwriting what Gentoo has put in there. With a bit of luck you should get a Grub bootmenu with options for all you OS.

Regards.

---

### Post by oldfred on 2013-03-01
Installs put the boot loader in the MBR of the drive so you can boot. Some give choices. Ubuntu only gives a choice with manual install and then no choice to not install.

What boot loader does Gentoo use, grub or grub2?

If you have the choice to not install, you should be able to boot into Ubuntu and run sudo update-grub and find all installs.

Or if you do install Gentoo's boot loader it should find other installs if grub2. Grub legacy was not so good about other installs and usually required boot stanzas to be added manually. If you then want Ubuntu to be in charge boot into Ubuntu and run this to install Ubuntu's boot loader to MBR. But Grub2 does remember where to reinstall on updates. So any major update may reinstall grub to MBR from any system you have installed.

       
#reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

---

### Post by DeanM1134 on 2013-03-01
Thanks, i'll definitely try these methods. Also, Gentoo seems to use grub 2 thankfully. I'll report back to this thread some other time when i've done a full install, because after reading a bit about Gentoo installations I was prepared to wait a few days for it to install so I opted to do it in a virtual machine first, hopefully saving myself some hassle from both grub and not having my computer for so long.

It took 10 minutes to install (and put me at a working desktop), and I didn't have to compile a thing. I'll probably keep it confined to VirtualBox for a bit to get a feel for Gentoo, but thank you for the help guys. I always love coming to the forums for advice.

---

