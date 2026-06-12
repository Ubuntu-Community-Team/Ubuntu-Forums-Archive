---
title: "UUID of the Ubuntu root partition changed"
date: 2013-07-01
forum: General Help
---

### Post by TheHimself on 2013-07-01
For some reasons I backed up my Ubuntu partition, reformated it and then copied the files back. Now the UUID of the partition has changed and Ubuntu won't boot. How can I fix this?

---

### Post by Impavidus on 2013-07-01
Boot from a live disk, mount the hard drive and modify your /etc/fstab (on the hard drive, not on the live disk) to match the new UUID.

---

### Post by TheHimself on 2013-07-01
I followed this to change the uuid in grub and fstab. Now it boots but gets stuck on the splash screen.

[http://askubuntu.com/questions/171446/how-to-fix-the-uuid-in-grub-after-restore-from-another-machine](http://askubuntu.com/questions/171446/how-to-fix-the-uuid-in-grub-after-restore-from-another-machine)

---

### Post by grahammechanical on 2013-07-01
The reformat has changed the UUID. You could try going to recovery mode and select the Grub option. It updates grub and puts you back at the recovery screen. You have a UUID in grub.cfg that does not match the UUID of the partition.

Do you still have that backup? Why not re-install and then just copy over the /home folders & files. Or better still use the Do Something Else option to install into that partition but do not mark the partition for format. That will leave the /home folder & files alone. Either way you should get a UUID into the grub.cfg and elsewhere that matches the UUID assigned by the installer.

Regards.

---

### Post by oldfred on 2013-07-01
You normally have to reinstall grub as it is looking for that UUID from the MBR & core.img files. Just changing in grub.cfg often is not enough.

You can use Boot-Repair to reinstall grub or your install liveDVD or flash drive.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)
    
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2
Grub2  info quick & full chroot version - method 3 - CHROOT:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by alphaamanitin on 2013-07-01
> **oldfred said:**
> You normally have to reinstall grub as it is looking for that UUID from the MBR & core.img files. Just changing in grub.cfg often is not enough.

You can use Boot-Repair to reinstall grub or your install liveDVD or flash drive.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)
    
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2
Grub2  info quick & full chroot version - method 3 - CHROOT:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

I would like to respectfully disagree, *with the following caveat*: I am not a person with any formal training in computer science nor a hardcore amatuer, and the following experience may be unique and/or no longer valid.

That said, I used to run linux (Ubuntu 9.04 and up to, but not including, 12.04; and debian version I cannot remember) from a usb hard drive.  For an unknown reason,  the UUID would change in grub (which was on the usb drive).  I found that if I interrupted the "auto" choice of grub and manually edit the boot UUID to the UUID I wanted (I had memorized it, it was that often) and would then boot.  At that point I would successfully boot and manually editted grub and saved it.  

As I said above, take that anecdote with the caveat in mind.

AlphaA

---

### Post by sisco311 on 2013-07-02
> **TheHimself said:**
> I followed this to change the uuid in grub and fstab. Now it boots but gets stuck on the splash screen.

[http://askubuntu.com/questions/171446/how-to-fix-the-uuid-in-grub-after-restore-from-another-machine](http://askubuntu.com/questions/171446/how-to-fix-the-uuid-in-grub-after-restore-from-another-machine)

Do you get any error messages? Try to press Esc and see if something shows up. 

Can you boot into recovery mode? If so, then try to run `dmesg' and see if it prints something relevant to the boot issue.


 BTW. Next time you restore your backup on a newly formatted partition, instead of reinstalling grub and editing fstab you could simply change back the UUID of the partition to the old one. Assuming it's an ext2/3/4 file system:
```
sudo tune2fs -U OLDUUID /dev/sdXY
```
Where OLDUUID is the original UUID and /dec/sdXY is the device name of the partition (i.e., /dev/sda1).

---

