---
title: "[SOLVED] GRUB problem"
date: 2008-01-23
forum: General Help
---

### Post by rob1984 on 2008-01-23
i'm dual booting gutsy and WinXP.

i've recently updated GRUB to fix a problem i was having and now it doesnt list my XP partition.

can anybody help me get windows back on the GRUB menu?

---

### Post by mannheim on 2008-01-23
You need to edit the file /boot/grub/menu.lst. For example, open up a terminal and type
```
sudo gedit /boot/grub/menu.lst
```
to start editing it. You need to add some lines similar to:

```
title		Microsoft Windows XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

You will need to change the "(hd0,1)" part to suit your situation. In this example, "hd0" means your primary hard disk, and the "1" means the **second** partition. If Windows is on the first partition of the  disk, you should type "(hd0,0)" instead.

If the menu.lst file has a line in it which looks like
```
### BEGIN AUTOMAGIC KERNELS LIST
```
then the best place to add the new lines is just above this line. That way, your changes shouldn't get wiped out by later updates.

---

### Post by rob1984 on 2008-01-23
worked perfectly thanks

---

