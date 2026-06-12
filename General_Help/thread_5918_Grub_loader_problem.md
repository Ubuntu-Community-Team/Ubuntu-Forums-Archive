---
title: "Grub loader problem"
date: 2004-11-23
forum: General Help
---

### Post by ikoyk on 2004-11-23
How can I uninstall grub loader from my system and install it in a diskette, so that I can boot ubuntu from there? I don't want to delay when I need to use my WindowsXp by selecting the OS from the Grub-loader. I tried to format the disk where ubuntu is and install it on another computer with no other OS, but I had problems starting my WinXp because of the GRub bootloader (Error), probably because my system tries to find the grub. What I can do in order to avoid formatting both of my disks?

---

### Post by arjaybe on 2004-11-23
You can edit /boot/grub/menu.lst so it defaults to your Windows, then reduce the delay before automatic booting to a tolerable length of time.

---

### Post by ikoyk on 2004-12-01
[QUOTE=arjaybe]You can edit /boot/grub/menu.lst so it defaults to your Windows, then reduce the delay before automatic booting to a tolerable length of time.[/QUOTE]
 How can I do this configuration to the menu.lst? I tried to open this file from Ubuntu text editor but I wasn't able to edit it, because it was in a read-only mode. I tried to do this also from the grub's options at start up, but I couldn't do it either. Can you help me?

---

### Post by Manu on 2004-12-01
You have to this as root with e.g. vim!
$ sudo vim /boot/grub/menu.lst

In short:
- Type **i** (now you can _i_nsert text)
- After inserting oder copying (see reference for command) you "exit insertion" with 'ESC'.
- Type wq! for writing and quit.

Commands in vim: [http://drumlin.thehutt.org/vi/](http://drumlin.thehutt.org/vi/)

---

### Post by littlegreenman on 2004-12-01
you can use vim, but I find gedit easier to use.

$ sudo gedit /boot/grub/menu.lst

---

### Post by adbak on 2004-12-01
You can use any of these editors, and some that I haven't mentioned, this is just a list off the top of my head:
vim
emacs*
gedit
nano

* - my personal preference

---

### Post by wallijonn on 2004-12-01
[http://www.ubuntuforums.org/showthread.php?t=6195](http://www.ubuntuforums.org/showthread.php?t=6195) :

insert a formatted floppy, start a Root Terminal

mkfs /dev/fd0
mount /media/floppy0
mkdir -p /media/floppy0/boot/grub
cp /boot/grub/stage1 /boot/grub/stage2 /boot/grub/menu.lst /media/floppy0/boot/grub
umount /media/floppy0

---

### Post by red58 on 2005-02-26
HELP!! installed ubuntu on a partition w/ GRUB boot and couldn't use the install cuz it wouldn't accept the password - tried everything - reformated the partition to try 'live' instead, but the boot loader got messed up, and now doesn't go past 'error 17'
how do I recover my boot sector? any help desperately requested!!!

Bill

---

