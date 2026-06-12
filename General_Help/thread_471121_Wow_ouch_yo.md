---
title: "Wow ouch yo"
date: 2007-06-11
forum: General Help
---

### Post by kialzyo on 2007-06-11
Well i installed ubuntu 7.04 with wubi on a hdd with xp and vista and now it has ruined the bootloader and automatically boots ubuntu and doesnt let me load windows xp or vista. pleas ehelp :(

---

### Post by CrazyGuy123 on 2007-06-11
Can you explain in more detail?

Do you get a menu asking you to choose between Ubuntu or Windows?
Did you install from Wubi, or did you burn the iso to a CD and install with that?

Are there any settings that you changed immediatly before or after installing wubi, particluarly todo with bootloaders or configuration files?

If you want a temporary fix and you have a floppy drive, may I suggest going to:
[http://bootdisk.com/bootdisk.htm](http://bootdisk.com/bootdisk.htm)
and select:
XP Quick Boot Diskette

(you need another windows machine to make the disk on (select the .exe download))
This should let you get back into windows, from where you may be able to fix it yourself if you know what changes may have been made, or ask again here for advice.

---

### Post by kialzyo on 2007-06-11
Well i was on windows then i decided to try ubuntu yet again and so i downlaoded the installer and it sintaleed the 7.04 fine and booted fine eveyrthing good but ther eis no bootloader to allow me to boot into windows.
And no i do not have a floppy disk drive i only have dvd/cd.
Help would be great:)

---

### Post by CrazyGuy123 on 2007-06-11
try the following:
switch the PC off
switch the PC on while tapping the F8 key until you get a menu.
A menu should show up (before the ubuntu splash screen)
If it has "start windows normally" select that.
If it has "Windows XP Home/Professional", select that.

If not, did you have any other type of linux installed in the past that might have had it's own bootloader?
If you don't get a menu, I'll have to re-think.

For the devs:
Is it possible that somehow grub got installed on this pc to the real MBR, if say the installer preseed failed?
How about if install returned to manual mode and the user selected "install LILO bootloader" from the menu?  (that entry is there if install fails during package installation and therefore can't install grub)
Is it possible that ubuntu was set as default and a timeout of zero applied in the windows bootloader?
Is it possible grub was already installed on this PC for another purpose (eg. recovery partition/second OS), and wubi overwrote menu.lst?

---

