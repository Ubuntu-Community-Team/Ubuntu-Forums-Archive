---
title: "error: no such partition. grub resque&gt;"
date: 2012-12-12
forum: General Help
---

### Post by kjoseph on 2012-12-12
Hi, every one, i really and humbly request for your assistance, i have windows 7 and ubuntu installed on my hp g7 notebook, while using windows i downloaded a partition manage rsoftware, while deleting partitions i deleted the boot partition by mistake, when i switch on now having shut down i get: 
error: no such partition. 
grub resque>

i  had just joined ubuntu and am not sure what i can do, please am humbly requesting for your assistance. thank you

---

### Post by oldfred on 2012-12-12
Welcome to the forums.

If you deleted the boot partition, you probably have to reinstall.

You can install Windows boot loader to get Windows working again.

See what this says.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
       How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

---

