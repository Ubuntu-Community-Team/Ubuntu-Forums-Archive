---
title: "Booting Error 15"
date: 2013-02-21
forum: General Help
---

### Post by Geunor on 2013-02-21
Hi.

I am having trouble booting up a laptop. I have installed SGD on a USB and booted up the bropken laptop whilst selecting the USB which starts up the Super Grub Disk to try and fix this problem. I have the following:

Super Grub Disk>Choose Language & Help>English Super Grub Disk>Gnu/Linux>Fix Boot of Gnu/Linux (GRUB)

and the following message shows up:

  Booting 'trying /grub/stage1 /boot/grub/stage1'
selectfile /grub/stage1 /boot/grub/stage1
Error 15: File not found
  Booting 'not lucky'
pause SGD has NOT succeeded :(
SGD has NOT succeeded :(

Does anyone know what this means and how to fix it please?

I need in depth step-by-step as I have no idea what some words mean and am new to Ubuntu, sorry.

Thank you for your time and help. =]

---

### Post by oldfred on 2013-02-21
If Supergrub cannot boot it, then you do have problems. :)

Error 15 is from grub legacy and usually is a conflict with grub2. Grub legacy has not been the standard since 9.04, but if you have upgraded since then you may have it. Or you may have found really old instructions on installing grub when everything really is grub2 now.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Geunor on 2013-02-22
> **oldfred said:**
> If Supergrub cannot boot it, then you do have problems. :)

Error 15 is from grub legacy and usually is a conflict with grub2. Grub legacy has not been the standard since 9.04, but if you have upgraded since then you may have it. Or you may have found really old instructions on installing grub when everything really is grub2 now.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

Thank you for your reply. 

Apparently you need the LiveCD to do some of what you have asked, which I do not have and cannot create here.

I will postpone this until I have a LiveCD.

Thank you for your help. 

Will re-post or bump when I have the disk.

---

