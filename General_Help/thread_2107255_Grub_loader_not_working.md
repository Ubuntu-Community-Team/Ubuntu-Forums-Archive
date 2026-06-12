---
title: "Grub loader not working"
date: 2013-01-21
forum: General Help
---

### Post by Lncredible on 2013-01-21
Hi guys,

History:

I had used the Windows Ubuntu quick installer to try ubuntu but insatlled the wrong version, so I deleted the ubuntu folder from my C:\. I then installed Ubuntu 10.4 from a USB drive and the installation was fine.

I forgot, however, to remove the windows startup entry for Ubuntu, which no longer worked because it referenced a place that didn't exist, which I did on the next boot.

Then I realised I wasn't being prompted by Grub to choose Win 7, mem test or ubuntu. It just boots into windows without any choice.

I read a few articles and someone suggested booting back into the USB and re-installing grub files, so I went ahead to try that. I booted into the USB and suddenly Grub pops up instead of the USB. 

Im not really sure how that happened. Anyway, I can't boot into the USB drive properly. I am certain that Ubuntu is on my hard disk, as I had to do the partitioning business.

Anyone experienced this before? How can I get grub to be the first priority upon restarts again?

Cheers,
Greg

---

### Post by oldfred on 2013-01-23
Best to see where everything is at:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

