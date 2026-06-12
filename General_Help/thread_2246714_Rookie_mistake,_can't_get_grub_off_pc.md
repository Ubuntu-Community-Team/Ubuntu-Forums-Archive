---
title: "Rookie mistake, can't get grub off pc"
date: 2014-10-02
forum: General Help
---

### Post by peter145 on 2014-10-02
Hey folks, like it says above, I got in over my head - I was running a dual-boot setup with Win7 and Ubuntu 14.04. I decided to just get a standalone machine for Ubuntu and take it off the other one, but after I restarted with a Windows CD, all I got on startup was "error: no such partition. Entering rescue mode... grub rescue> deb"

I popped out the HD and did a full format from another machine, but the error message persists. I've tried changing boot order to run from the CD drive with both an Ubuntu disc and a Windows 7 disc, and always get the same error.

If anyone can shed light on this, I'd appreciate it. I apologize if this has been posted elsewhere, but I've looked high and low and can't find anything with these exact issues.

Thanks, all.

---

### Post by oldfred on 2014-10-02
You need to install the Windows boot loader before you delete Ubuntu. The grub boot loader in the MBR expects to find more of grub in the Ubuntu partition.

You can use Ubuntu live installer or a Windows repairCD or flash drive to restore a Windows boot loader. Make sure boot flag is on the Windows partition with Windows boot files.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

Boot-Repair run from the Ubuntu live installer can also install a Windows type boot loader to the MBR.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by grahammechanical on 2014-10-02
Just a point for future reference. You are posting in the section called Ubuntu Development Version but you are using a released version of Ubuntu. A version that is no longer under development. This section is for those of us who are testing the next version of Ubuntu that is under development and that is Utopic Unicorn (14.10)

Regards.

---

### Post by QIII on 2014-10-02
Moved to General Help

---

