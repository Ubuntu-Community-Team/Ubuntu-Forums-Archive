---
title: "Problem with installing ubuntu 12.10 GRUB failed"
date: 2013-08-05
forum: General Help
---

### Post by ThulasiS on 2013-08-05
I am trying to install ubuntu 12.10 on my system. I formatted the
system with ubuntu and installed but the final message was GRUB
installation failed a fatal error, what to do now? I am not worrying
about any data or other but I need to install it. I tried to reinstall
but not installed, error message: no root file found. Even after
selecting partition options and in all drives saying no root file
found. [COLOR=#888888]What can i do now?? Please help me in solving this problem. Currently no OS in system to operate.
And help me in partitioning the hard disk too because my old partitions lost because of this installation.
[/COLOR]

---

### Post by oldfred on 2013-08-05
With manual install you do have to specify which partition is / (root), what format usually ext4. If swap already exists it finds it automatically. If you have an existing separate /home you also have to choose which partition, but DO NOT check the format box.

If not booting:
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

