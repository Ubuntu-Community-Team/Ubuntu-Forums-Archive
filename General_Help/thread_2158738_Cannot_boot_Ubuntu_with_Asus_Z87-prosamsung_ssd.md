---
title: "Cannot boot Ubuntu with Asus Z87-pro/samsung ssd"
date: 2013-06-30
forum: General Help
---

### Post by MikeCyber on 2013-06-30
HI
installed win8 than 13.10 but I cannot boot/show grub. I've added a boot entry in easybcd but still no luck. :(
Thanks
PS: hd is a samsung ssd

---

### Post by oldfred on 2013-06-30
With new systems, you have both UEFI & BIOS. And how you boot installer is how it installs. But you cannot easily dual boot unless both are UEFI or both are BIOS. You only can then dual boot by going into UEFI/BIOS and turn it on or off if both are not same mode.

Best to see details.
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by MikeCyber on 2013-07-01
Thanks, boot-repair fixed the uefi problems on 13.04. (was not yet available in 13.10)

---

### Post by MikeCyber on 2013-07-20
Still it hangs at: loading initial ramdisk
But not if I boot Win8 and go back.
Any ideas? I've updated Nvidia drivers without success.
Thanks

---

### Post by oldfred on 2013-07-20
I do not know about RAMdisks? Are you mounting something at boot time via fdisk? Or is this related to Intel SRT?

---

### Post by MikeCyber on 2013-07-31
Solved, bios was in legacy mode.

---

