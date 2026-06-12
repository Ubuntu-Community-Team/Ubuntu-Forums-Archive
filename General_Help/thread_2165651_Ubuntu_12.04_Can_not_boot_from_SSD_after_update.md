---
title: "Ubuntu 12.04 Can not boot from SSD after update"
date: 2013-08-05
forum: General Help
---

### Post by tszchinglam on 2013-08-05
Hi guys,

My system was working just fine like 10 mins ago when I applied the updates and was prompted to restart.

When the system rebooted and got past the bios screen, it said it can't find the boot device.

So I rebooted again and went into the BIOS, everything was there, the motherboard was able to identify my boot disk which is a SSD.

I wonder if the update has accidentally wipe the whatever GRUB/UEFI settings (I remembered that I had a tough time setting it up).

Would anyone give me some advices?

Charles.

---

### Post by oldfred on 2013-08-05
May be best to see details.

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

