---
title: "restore kubuntu entry to grub"
date: 2007-09-27
forum: General Help
---

### Post by guitarmaniac on 2007-09-27
I just installed PCLinuxOS on my computer yesterday. When it installed it over wrote my grub.
The new grub found my windows partition, but not my Kubuntu one.
I don't know too much about bootloaders so how is the easiest way to restore my Kubuntu entry?
Thanks in advance :guitar:

---

### Post by logos34 on 2007-09-27
Kmenu > Applications > File Tools > File Manager-Super User Mode

Open your grub config file using text editor like kate or kwrite:

# **kwrite /boot/grub/menu.lst**

add entry for kubuntu:
> 
title		Kubuntu 7.04 Feisty Fawn
root		(hd0,y) ---> where y=partition #
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/hdxy ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic

Ex: if kubuntu were on first (ide) drive, partition 1, then you would use '**(hd0,0)**' and 'root=/dev/**hda1**'.  If sata drive, 'sda1'.

---

