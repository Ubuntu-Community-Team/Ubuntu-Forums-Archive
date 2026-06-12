---
title: "QEMU with Windows XP UPGRADE CD"
date: 2007-05-13
forum: General Help
---

### Post by funnyguyfunnyguy on 2007-05-13
I am trying to install Windows XP Home Edition with QEMU. I have an upgrade CD rather than the full version, and  when I reach the screen which asks to "insert [my] Windows NT 3.51 Workstation, Windows NT 4.0 Workstation, Windows 2000 Professional, Windows 95, Windows 98, or Windows Millennium CD into [my] CD-ROM drive" QMEU/Windows cannot find the CD, despite having it in the drive. Any ideas?

---

### Post by dannyboy79 on 2007-05-14
you just need to switch to the qemu console, Ctrl-Alt-2, and tell it to eject the cdrom and then tell it where it is after you put in the new cd just like this guy ([http://www.weiqigao.com/blog/2006/02/20/qemu_the_open_source_processor_emulator.html](http://www.weiqigao.com/blog/2006/02/20/qemu_the_open_source_processor_emulator.html)) did when he installed a multi-disk windows 3.1 operating system. so after you get to the console, use something like this to tell qemu to eject the cdrom and then load it.
(qemu) eject fda
(qemu) change fda /dev/fd0
then after you ahve done this, then issue ctrl-alt-1 and you should return to the install.
PS (Don't try to remove the cd yourself, when the installler asks you for the next cd, don't push the button on your cdrom, use qemu to eject it. if the qemu isntaller ejected it for you than that may be ok, but still issue the eject command. you can type info block to see if it sees the new cd before you hit ctrl-alt-1. good luck

---

