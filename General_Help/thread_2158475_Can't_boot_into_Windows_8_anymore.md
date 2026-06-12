---
title: "Can't boot into Windows 8 anymore"
date: 2013-06-29
forum: General Help
---

### Post by Snitz on 2013-06-29
Hello,

I used to run Windows 8 along side Linux Mint and they worked peacefully together but ever since I dropped mint in favor of Ubuntu, I can't boot into Windows 8 anymore.

The OS appears on the boot loader on startup but when I choose it, it redirects back to the boot selection menu.

---

### Post by oldfred on 2013-06-29
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

### Post by Snitz on 2013-06-29
Thank you, that did it.

---

