---
title: "over wrote grub on sda1 for new os on sda2 sda1 no longer appears in grub.."
date: 2015-01-20
forum: General Help
---

### Post by jeffmezz on 2015-01-20
[COLOR=#9A9A9A][FONT=lucida grande]Operating System: UbuntuStudiox86_64 low Latency  14.04 kernal 3.13.0-35[/FONT][/COLOR]
[COLOR=#9A9A9A][FONT=lucida grande]Graphics: Geforce GTX760[/FONT][/COLOR]
[COLOR=#9A9A9A][FONT=lucida grande]RAM: 6Gb[/FONT][/COLOR]
[COLOR=#9A9A9A][FONT=lucida grande]Processor: i3 3240[/FONT][/COLOR]
[COLOR=#9A9A9A][FONT=lucida grande]MotherBoard: MSI Z77A-G45[/FONT][/COLOR]
[COLOR=#9A9A9A][FONT=lucida grande]USB 3.0[/FONT][/COLOR]

Ok so I decided to upgrade my hard drive and install a second install of trusty on sdb1....Now when grub boots I only have the new os available on the boot list. Is there a way to add sda2's information to grub to recognize it as a bootable os...I'm at a loss because I was running a VM with lots of information that I cannot access through direct drive access from OS 2 on sdb1.

Steps I've tried

sudo update-grub
sudo install-grub sda

Also tried to install Burg on sda

In Gparted I've noticed a 1Mib partition called unknown flagged as bios_grub and it has a red exclamation mark...

---

### Post by yancek on 2015-01-20
> 
In Gparted I've noticed a 1Mib partition called unknown flagged as bios_grub and it has a red exclamation mark... 

That's for a sytem using the MBR BIOS with GPT partitioning rather than UEFI with GPT.  Did you install both releases of Ubuntu as GPT with no efi partition.  I believe you need both the same either, EFI or MBR.  The red exclamation mark would make me wonder about this.

---

### Post by oldfred on 2015-01-20
The red exclamation point is only because it is unformatted which is required, so gparted cannot parse it.  It is ok.

But as yancek says, both installs need to be BIOS or both UEFI. You can dual boot but only from UEFI menu and maybe have to turn on/off UEFI mode or CSM/BIOS mode to boot install in that mode.

---

