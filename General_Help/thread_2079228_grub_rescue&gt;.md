---
title: "grub rescue&gt;"
date: 2012-11-01
forum: General Help
---

### Post by thequick on 2012-11-01
During a software update/upgrade, I inadvertently pulled the plug on my laptop. Now when I go to reboot, all I get is this message and my laptop is useless:
 
ELF header smaller than expected.
grub rescue>
 
Any suggestions?

---

### Post by oldfred on 2012-11-01
You may have to chroot into your system to repair or finish updates. But lets see if you can boot and finish the updates from your system. You can run the suggested repairs and if they do not work post BootInfo link.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

