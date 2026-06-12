---
title: "Installing Ubuntu over a network"
date: 2015-04-03
forum: General Help
---

### Post by Kpenguin on 2015-04-03
Hi everyone,
I've got a 15 year old Dell that I'd like to install Ubuntu 14.04 on. It only has a bootable CD and floppy drive, and can't boot from USB. I'm rather at loss as to how to install it, but in the boot menu, it has "boot from LAN" as an option. Is it possible to install Ubuntu using this feature? If so, how do I do that?
Please note that I'm a relative newbie at Linux.
Thanks!

---

### Post by nerdtron on 2015-04-03
15 year old - Ubuntu 14.04

Is that a desktop? you sure the specs can run Ubuuntu 14.04?

---

### Post by Kpenguin on 2015-04-03
> **nerdtron said:**
> 15 year old - Ubuntu 14.04

Is that a desktop? you sure the specs can run Ubuntu 14.04?
Yes, it's a desktop. I'm pretty sure it can run 14.04, because I had another computer that was even older with lower specs that ran it just fine. Its got a 1.7 ghz single core processor with 1gb of memory and a relatively high end graphics card.

---

### Post by deadflowr on 2015-04-03
You'd be better off downloading the smaller mini.iso from here
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It's basically a net installer, but you start properly with a base to connect to Ubuntu server's.
You can also be to choose a more appropriate desktop environment for the machine
(15 years old might be a little old for normal ubuntu, perhaps something like Lubuntu-desktop or even the mate desktop, if available, would suit it better.)
--BUT, if you think the specs are good for Ubuntu, then choose ubuntu-desktop when that options comes, late, in the installation.
(Installing the desktop environment is usually the last major step in the installer)

Installing via boot from LAN is possible, but would require you to either setup a dhcp-boot from another machine and properly configure the installer.
A rather complex mess, IMO.
(from here
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)
you could see what it would entail, if you truly wanted to go the route.)

Or have the linux bootloader(called grub) installed, and download the appropriate files following this guide
[https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet](https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet)
Of course, though, that requires grub.

But the mini.iso is really tiny, only around 32MB or so, so it fits snug on a cd.
Do you have any method to download and burn a rather small cd image?
(like on a second machine somewhere?)

The only true caveat to all network install methods is having a functional network card.

---

### Post by bab1 on 2015-04-03
> **Aaron_Wolfe said:**
> Yes, it's a desktop. I'm pretty sure it can run 14.04, because I had another computer that was even older with lower specs that ran it just fine. Its got a 1.7 ghz single core processor with 1gb of memory and a high end graphics card.

You will not be able to install anything on this host without adding a hard drive.  Your other option is to create a PXE bootable image on another machine that your desktop uses to boot from (i.e a PXE server).  This is what "boot from LAN" means.  A PXE server is not a trivial matter.  You are better off installing a hard drive in the desktop or removing the "high end graphics card" and getting a new computer.  The specs for the desktop barely match the minimum needed to run Ubuntu (Unity or Gnome).

---

### Post by Kpenguin on 2015-04-03
Thanks everyone for your help. I'll probably just go with the mini installer. I have two other PCs that I can burn from. The computer I'm wanting to install on is basically my hobby.

---

### Post by deadflowr on 2015-04-03
A helpful hint for installing the mini.iso is when you get to the package installation screen, which will list packages like ubuntu-desktop and kubuntu-desktop, and so on.
Use the spacebar to select the packages before you hit enter, otherwise it'll think you're done, and you'll boot into a text login prompt.

---

### Post by bab1 on 2015-04-03
> **deadflowr said:**
> A helpful hint for installing the mini.iso is when you get to the package installation screen, which will list packages like ubuntu-desktop and kubuntu-desktop, and so on.
Use the spacebar to select the packages before you hit enter, otherwise it'll think you're done, and you'll boot into a text login prompt.

From the OP >  It **only** has a bootable CD and floppy drive, and can't boot from USB

Where do you want the OP to install the OS?  A CD is read only and a floppy drive is waaaaaay too small.  What am I missing here?

---

### Post by grahammechanical on 2015-04-03
Me thinks the OP was referring to his options for install media. The mini iSO is less than 40MB in size so it fits on to a CD disc. And since the OP has a machine with a CD drive and a BIOS that will boot from a CD drive then using the mini ISO is a valid option for installing Ubuntu on this machine. The install actually does take place over a network - Its the internet network. Everything is downloaded from the Ubuntu servers.

Regards.

---

### Post by deadflowr on 2015-04-04
> **bab1 said:**
>  Where do you want the OP to install the OS?  A CD is read only and a floppy drive is waaaaaay too small.  What am I missing here?


Me:
> But the mini.iso is really tiny, only around 32MB or so, so it fits snug on a cd.
**Do you have any method to download and burn a rather small cd image?**
**(like on a second machine somewhere?)**
OP: 
> Thanks everyone for your help. I'll probably just go with the mini installer. **I have two other PCs that I can burn from.** The computer I'm wanting to install on is basically my hobby

---

### Post by bab1 on 2015-04-04
> **deadflowr said:**
> Did you read the rest of my post or the OP's reply?
Me:

OP:Of course I did.  It was (and still is) unclear as to what device  the OP is INSTALLING the working OS (HDD or SSD or ...)  I understand the download of a mini.iso.  The OP is ambiguous as to the install location  HDD or SDD or ...).

But who am I to question ambiguous questions or answers that assume something that is not stated.  Well; 20+ years of experience in IT tells me that this can be a problem.  In general I don't guess, I confirm the facts at hand.

You seem to seem to have a problem with my asking for clarification.  The question was asked (by me) and answered (by @grahammechanical).   What's wrong with that?  Relax; I'm not questioning your answers, rather I'm asking for the OP to think about the composition of the original question asked.

---

### Post by Kpenguin on 2015-04-05
> **bab1 said:**
> From the OP 

Where do you want the OP to install the OS?  A CD is read only and a floppy drive is waaaaaay too small.  What am I missing here?

It has a hard drive. I was referring to options to boot from. :)

---

