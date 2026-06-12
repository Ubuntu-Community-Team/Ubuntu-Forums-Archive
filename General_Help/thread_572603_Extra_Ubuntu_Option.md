---
title: "Extra Ubuntu Option"
date: 2007-10-10
forum: General Help
---

### Post by McTricks on 2007-10-10
I have installed Ubuntu and XP on my PC.

When I start my PC, there is a duplicate option for Ubuntu, so I see this

Ubuntu ...
Ubuntu Recovery mode...
Ubuntu ...
Ubuntu Recovery mode...
Memtest+ ...

What should I do to get rid of the second Ubuntu, and the second recovery mode?

---

### Post by FRuMMaGe on 2007-10-10
Are they both the same?  Read the line carefully.

Did you upgrade the kernel?  If so, then the new one is the new upgraded kernel and is nothing to worry about.

---

### Post by por100pre1 on 2007-10-10
They should be the original installation Linux kernel and an updated one above, each one with a recovery mode.

---

### Post by McTricks on 2007-10-10
Ah, they are different, but, is there a way to hide the old one?

---

### Post by dreadlord_chris on 2007-10-10
> **McTricks said:**
> Ah, they are different, but, is there a way to hide the old one?
Yes, but it is generally recommended that you keep at least the last kernel option available - in case you come accross problems with the updated kernel.

```

sudo nano /boot/grub/menu.lst

```
look for the line that starts:
```

# howmany=

```
I do believe the default is *# howmany=all* - just change it to:
```

# howmany=1

```
GRUB will now only show the latest kernel to boot from.

again, I recommend that you instead make it *# howmany=2* - so you always have the previous kernel available should any problems occur

---

### Post by Ub1476 on 2007-10-10
I that if you go to.. 

```
sudo gedit /boot/grub/menu.lst

```

..and add a ## in front of the kernel(s) you want to hide, it will be hidden.

---

### Post by dashnak on 2007-10-10
You could erase it from your menu.lst, or you could use a gui to alter GRUB settings, although I can't really remember its name.
Edit: Wrote this while everybody else was posting, don't mind it.

---

### Post by McTricks on 2007-10-10
ok... thanks

---

