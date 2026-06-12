---
title: "Boot Help Please!"
date: 2013-03-17
forum: General Help
---

### Post by Tony T on 2013-03-17
No boot device found when trying to boot. I was getting the grub> prompt, but then I tried "Boot Repair" and now nothing. Boot Repair had me issue the following commands.:

```
sudo chroot "/mnt/boot-sav/sda2" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sda2" apt-get install -fy
sudo chroot "/mnt/boot-sav/sda2" apt-get purge -y --force-yes grub*-common shim*
sudo chroot "/mnt/boot-sav/sda2" apt-get install -y --force-yes grub-efi
```


When done, it repsonded with:
> Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/5621586/](http://paste.ubuntu.com/5621586/)

Now I can't even get the grub prompt! I can get into my ubuntu drive from a live CD and the files look ok.

One thing I noticed when doing the Boot Repair was this terminal message:
> Creating config file /etc/default/grub with new version
Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.
Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.
Installation finished. No error reported.
Setting up grub-efi (1.99-21ubuntu3.9) ...

Please help! What should I try next? I'm a newbie so please be explicit! Thank you!

---

### Post by Tony T on 2013-03-17
Bump. . . any ideas or maybe direct me to some other forum that may help. Pretty Please!

---

### Post by oldfred on 2013-03-17
It seems like Boot-Repair was converting a BIOS install to UEFI install. 

Is this a Windows 8 system with secure boot.

Have you turned off secure boot, fast boot and are you booting from UEFI and choosing ubuntu?

Is this the procedures you followed?
 
You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

---

### Post by Tony T on 2013-03-17
Thank you very much oldfred!

> **oldfred said:**
> It seems like Boot-Repair was converting a BIOS install to UEFI install. 

Is this a Windows 8 system with secure boot.


No, this is a single drive system with ubuntu 12.04.2 LTS only. No Windows! I don't understand why Boot-Repair was converting a BIOS install to UEFI install?

> 
Have you turned off secure boot, fast boot and are you booting from UEFI and choosing ubuntu?

Yes, but it was working fine before with fast boot.

> 
Is this the procedures you followed?
 
You will need to use the 64 b 64 bit version of 12.10 or 12.04.2it version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

No, I installed the 64 bit version of 12.04.2 LTS using a  flash drive but not in UEFI mode. EFI is the confusing part, there was no EFI install as far as I know.  Any additional thoughts?

Thanks,
Tony

---

### Post by Tony T on 2013-03-17
UPDATE:

> 
 EFI is the confusing part, there was no EFI install as far as I know.  Any additional thoughts?


Correction: My motherboard is using UEFI, howerver, installing Ubuntu dosen't give me a UEFI option, it is automatic. Should I just try a grube2 MBR install?

---

### Post by oldfred on 2013-03-18
You should be able to go into UEFI menu and choose to boot ubuntu. It may still be set in another default boot mode.

It installs in the mode you boot installer flash drive. The UEFI/BIOS menu should show two options, one UEFI and the other BIOS/Legacy/CSM or whatever. Then it installs in that mode.

If only Ubuntu you can have gpt partitioning with BIOS boot but have to have the bios_grub partition. With UEFI boot you have to have the efi partition.

Both Windows & Ubuntu use the same efi partition and you still show the Windows boot files in the efi partition, so that is why Boot-Repair is trying to include those in grub's menu.

Have you turned secure boot off & fast boot off. A few systems only let you turn fast boot off from Windows boot menu and if you do not turn it off there, you brick system as if Windows does not boot you cannot get into UEFI menu to even boot a Windows repair.

Windows only boots from gpt partitioning with UEFI or with UEFI only can have gpt partitioning.

---

### Post by Tony T on 2013-03-19
Thanks oldfred, I trired many things such as trying to manually install grub2 with these commands:

> 
sudo mkdir -p /dev/sda1 /mnt/boot/efi
sudo mount /dev/sda1 /mnt/boot/efi #sda1 is my efi partition
sudo mount -t vfat -o rw,users /dev/sda1 /mnt/boot/efi
sudo mkdir -p /mnt/boot/efi/grub
cd /home/ubuntu/Downloads/grub-2.00/grub-core
sudo cp grub.efi *.mod *.lst /mnt/boot/efi/grub
sudo touch /mnt/boot/efi/grub/grub.cfg
../grub-probe --target=device /boot/efi/grub/grub.efi

But in the end nothing seemed to fix it. I had access to all my files, so I just copied my home directory and reinstalled ubuntu 12.04.

I'm convinced the problem had to do with the bios UEFI boot as you suggested, however, I couldn't solve it. So anyway thanks again for all your help, I'm up and running on a new ubuntu install.

---

