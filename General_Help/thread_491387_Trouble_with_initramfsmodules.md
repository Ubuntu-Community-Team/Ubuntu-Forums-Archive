---
title: "Trouble with initramfs/modules"
date: 2007-07-03
forum: General Help
---

### Post by Pde on 2007-07-03
After a lot of trouble installing Feisty (getting it to boot) I found a workaround that involves adding "piix" to initramfs-tools/modules and running "sudo update-initramfs -u". I am fairly new to Linux and I can't figure out how to do this, as the modules file is read-only and I can't change the permissions. How do I add something to the modules file?

---

### Post by MCSE_Crossover on 2007-07-03
sudo gedit initramfs-tools/modules

append piix within that file

FILE --> SAVE --> QUIT

sudo update-initramfs -u

You don't need to change permissions, you just need to edit the file with elevated privelages (sudo)

---

### Post by Pde on 2007-07-03
Doing that I get:
** (gedit:11410): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.

---

### Post by Pde on 2007-07-03
Wait, I figured that out, I had to specify /etc/initramfs-tools/modules, but now it says 
sudo: /etc/initramfs-tools/modules: command not found
if I don't put sudo, it says 
bash: /etc/initramfs-tools/modules: Permission denied

---

### Post by Pde on 2007-07-03
Wait, I got it, thanks.

---

