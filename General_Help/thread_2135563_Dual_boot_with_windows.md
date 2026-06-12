---
title: "Dual boot with windows"
date: 2013-04-14
forum: General Help
---

### Post by leilton on 2013-04-14
I hope this has not been asked, and answered before, have looked and can´t find it,  so here go&#347;

Have dual booted windows xp and xubuntu 12.10,what I would like to do, is replace xp with vista, but have an idea that this will mean havint to reinstall xubuntu again, no don´t know where thought came from, seem to remember someone saying that you cannot delete and replace as you can in Linux.

Any help would be appreciated.

---

### Post by oldfred on 2013-04-14
Anytime you make system changes, you need good backups.

You should just have to reinstall the grub2 boot loader to the MBR. When you install Windows it overwrites the MBR with the Windows boot loader.

       [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

---

