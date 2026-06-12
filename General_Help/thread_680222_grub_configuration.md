---
title: "grub configuration"
date: 2008-01-27
forum: General Help
---

### Post by wolfy1220 on 2008-01-27
I currently dual boot with grub. 
I run win xp and ubuntu 7.10

I need to know if there is a way I can change the default os to boot.
Currently it auto boots into ubuntu if no selection is made, can I change it to auto boot into xp?

I use xp a bit more than ubuntu and I tend to walk away for a moment when I turn on the pc, come back and its in ubuntu when I need xp.

---

### Post by Ptero-4 on 2008-01-27
change the number in the "default" entry in your /boot/grub/menu.lst (the numbering starts in 0 which points to the topmost kernel entry and goes down through every kernel or OS entry (skipping separators and the "memtest86" entry).

---

### Post by wolfy1220 on 2008-01-27
i found the file and am not sure what to change the number too.
I have:
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

I tried to change it and save it but it told me i dont have the permissions to change it???
Im not even sure what to change it to?

---

### Post by confused57 on 2008-01-27
> **wolfy1220 said:**
> i found the file and am not sure what to change the number too.
I have:
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

I tried to change it and save it but it told me i dont have the permissions to change it???
Im not even sure what to change it to?
Here's how to edit your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

You can copy & paste your Windows entry to just above the line ###BEGIN AUTOMAGIC KERNELS LIST or you can change the default number:
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

---

### Post by wolfy1220 on 2008-01-28
The copy and paste worked for me, thanks alot confused and ptero-4. appreciate the help.

---

