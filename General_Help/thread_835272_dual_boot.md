---
title: "dual boot"
date: 2008-06-20
forum: General Help
---

### Post by entaroadun on 2008-06-20
I have ubuntu 8.04 installed and i need to make an instalation of windows xp how do i do this without loosing my bootloader and without reinstaling ubuntu ?

---

### Post by ajgreeny on 2008-06-20
You can go ahead and install XP and then reinstall grub with the live CD as follows:-
Boot into the ubuntu live CD
open a terminal and run :
    sudo grub
This gets you to a simple grub command line.
Then:
    find /boot/grub/stage1
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
    root (hd?,?)
[like : root (hdo,1) ,probably]
then:
    setup (hd0)
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.

You may need to change the line
root  (hd0,0)
if you have changed where you have XP, but if it is exactly where it was before, ie hda1 (or sda1 if you have sata drive) the old dev name in menu.lst should still be OK.  Give it a try and good luck.

---

