---
title: "Kernel Hold Command, Command to undo--necessary?"
date: 2014-10-27
forum: General Help
---

### Post by SciGuy1872 on 2014-10-27
I entered the following command: 

anthony@anthony-desktop:~$ sudo grub-set-default 3.2.0-70-generic-pae

I was afraid that the HWE update would break the Nvidia installer, but I was told the 3.2-xx will still be updated for security fixes, with no chance of bringing in the Trusty kernel, unless I told the computer to do the HWE.  So, I was wondering if I'm okay--is the kernel still going to be updated  or do I need to issue another command to cancel the hold? I also tried Synaptic to lock, but it doesn't, so I'm okay there; but I did enter this command in the terminal, so it may be different.


Thanks for your time and help.

---

### Post by ian-weisser on 2014-10-27
The grub-set-default command will not prevent a kernel version from being updated or removed.
The command has nothing to do with package management or updates.

All the command will do is specify which kernel will be the default for grub to boot from...if that kernel happens to be installed.

---

### Post by SciGuy1872 on 2014-11-04
Okay, thanks.  I want the latest kernel to be used because of security--wouldn't I have to enter a command to cancel the hold so that 3.2.0-70-generic-pae isn't always used as the default?

---

