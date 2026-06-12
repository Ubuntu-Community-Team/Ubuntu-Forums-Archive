---
title: "Booting windows first"
date: 2015-10-01
forum: General Help
---

### Post by christopher40 on 2015-10-01
On my PC I have currently Windows installed. It should also remain like that because sometimes other people use my PC as well. But when i am programming I would like to switch to Ubuntu. If I install Ubuntu the bootloader chooses to start Ubuntu if you dont go down to select Windows. Well I want it to be the other way round. It should start Windows if I press no buttons. Any idea how I can do it?

I was also thinking about installing Ubuntu on an external SSD drive. Are there any bigger disadvantages for developing. I would connect it via USB 3.0. Or is it better to use an internal hard drive and just change the bootloader?

---

### Post by Dennis N on 2015-10-01
You can do this by editing **/etc/default/grub**

The first line, **GRUB_DEFAULT=0** controls which entry boots automatically. 0 = first OS entry, 1 = second OS entry, etc. Change this value to change which OS boots automatically. After making a change, run **sudo update-grub** to update the grub settings.

Example:
If you change the value to 1, the menu order itself will not change, but the * should now be at the 2nd Grub menu entry, and it will boot instead of the first entry.

Note: If you get the wrong one marked by *, boot back into Ubuntu and redo.

---

### Post by oldfred on 2015-10-01
I do not think USB connections support trim. So using an external SSD may eventually have issues.

You can use number as Dennis N shows you. But you can also use description, but it must be exact, so you have to copy & paste.

       [https://help.ubuntu.com/community/Grub2/Setup#A.2BAC8-etc.2BAC8-default.2BAC8-grub](https://help.ubuntu.com/community/Grub2/Setup#A.2BAC8-etc.2BAC8-default.2BAC8-grub)
find your windows entry in grub.cfg and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default  here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new :
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

