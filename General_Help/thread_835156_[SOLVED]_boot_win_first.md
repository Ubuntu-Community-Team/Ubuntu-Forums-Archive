---
title: "[SOLVED] boot win first"
date: 2008-06-20
forum: General Help
---

### Post by microworm on 2008-06-20
Hello,
My computer has Windows Vista and i have recently installed Ubuntu 8. So i have Vista and Linux on the one computer.
The problem is that Linux boots by default unless i choose vista from the list before they boot. I want Vista to boot before Ubuntu unless I choose to boot Linux. 

Can anyone help me?

---

### Post by dracayr on 2008-06-20
use startupmanager or simply edit /boot/grub/menu.lst (or /grub/menu.lst if you installed without /boot)

dracayr

---

### Post by nnamdi on 2008-06-20
you can do that simply go to your boot menu list and then edit

---

### Post by Victormd on 2008-06-20
first, open a terminal and open your grub menu:
```
sudo gedit /boot/grub/menu.lst
```
Now, there are 2 ways about doing this:
1. Change the Default Number at the top of the file from 0 (zero) to the number on the menu that corresponds to Windows (when you start, if you have 3 lines of OS, Windows being the last, you will replace the 0 by 2).
> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**[COLOR="Red"]default		2[/COLOR]**

2. Change the Default Number from 0 (zero) to saved (actually write saved - notice the warning if you have a RAID setup)
> # WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**[COLOR="Red"]default		saved[/COLOR]**
Scroll down and make sure you have a "savedefault" line under the windows entry like such:
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
[COLOR="Red"]**savedefault**[/COLOR]
makeactive
chainloader	+1

There, now windows will be the first boot. For this second option, the first time you reboot you will need to choose Windows, then it will be saved as the default.

Hope this helps

---

### Post by microworm on 2008-06-20
Thanks for that, except now its telling me i cant save the menu file because I dont have permission. How do i gain permission?

---

### Post by dracayr on 2008-06-20
I guess you didn't use the command Victormd suggested (sudo gedit...). type ```
gksudo gedit /root/grub/menu.lst
``` in a terminal and edit the file.


dracayr

---

### Post by microworm on 2008-06-20
Oh yes, right! I didnt open the file from the terminal. Ok its working now. Thanks heaps for your help guys!

---

### Post by Victormd on 2008-06-20
Any time...
Don't forget to mark the thread as solved under "Thread Tools". :)

---

