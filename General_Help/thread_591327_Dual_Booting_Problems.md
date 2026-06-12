---
title: "Dual Booting Problems"
date: 2007-10-25
forum: General Help
---

### Post by Dorotheos on 2007-10-25
OK, im as new as can be here. I installed ubuntu. then re-installed windows xp. Couldn't get ubuntu to boot, looked for help here:
Found these commands:
sudo grub
find ...
setup hd(...
quit

or something like that..
Now when Grub runs it doesn't recognize the windows install!
I want to be ablt ot pick between the two. How do i do this?

---

### Post by benerivo on 2007-10-25
Open /boot/grub/menu.lst and add these lines to the bottom of the file and reboot...

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

(this example presumes that windows was installed on the first partition of your primary hard drive)

---

### Post by Dorotheos on 2007-10-25
Actually i downloaded Ubuntu first! Then windows... so now what?:confused:

---

### Post by benerivo on 2007-10-25
So you installed ubuntu, then installed windows which wrote over the grub boot loader. You then restored grub (say exactly how you did this), but it is not picking up windows. Is this right?

If so, you may not have windows on "root (hd0,0)". Whatever the case, go in to Ubuntu and enter this in a terminal```
sudo fdisk -l
```Try to work out which partition contains windows. If it is hda1 then windows is on (hd0,0). If it is on hda4 then windows is on (hd0,3) - Eg. Whatever partion it is on, just take away 1 to get the correct second digit. Then run```
sudo gedit /boot/grub/menu.lst
```Try adding the lines as mentioned above, using the correct second digit.

---

