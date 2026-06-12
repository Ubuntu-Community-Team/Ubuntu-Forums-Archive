---
title: "Worried I lost Windows 7"
date: 2013-05-07
forum: General Help
---

### Post by 3mutts on 2013-05-07
Ok I was stupid and shut down my computer before the Ubuntu installation was complete, I come back to a grub rescue screen (I installed Ubuntu over Linux Mint), I'm worried that I lost Windows 7 in the process. I hope that I installing Ubuntu 13.04 correctly will fix this. If not can any one give me options to fix this, I really don't want to lose Windows 7!

EDIT: Never mind, reinstalling GRUB fixed it, this can be locked, sorry for this stupid post.

---

### Post by cruz12141214 on 2013-05-07
well that depends, if you installed it on a separate partition/ HDD you should be fine, if you used your windows partition well then you lost it



but either way reinstalling Ubuntu will tell you, grub2 should find windows if its there

---

### Post by oldfred on 2013-05-07
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

