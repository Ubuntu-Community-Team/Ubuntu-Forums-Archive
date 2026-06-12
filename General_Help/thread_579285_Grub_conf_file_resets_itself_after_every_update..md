---
title: "Grub conf file resets itself after every update."
date: 2007-10-18
forum: General Help
---

### Post by Sparky222B on 2007-10-18
This is **so** annoying. Every time I run System Update and the kernal or Ubuntu version is incremented, Grub.conf is edited, my default partition is reset and my other boot partitions are removed.

Isn't there any way to 'lock' this file..aka make it read only to the system?

Thanks

---

### Post by Jose Catre-Vandis on 2007-10-18
It is read only to the system, but you give it permission when you do the upgrades. What is the set up for your system, this might give a clue as to why it is resetting. If your default boot partition is not in the "auto-magic" section of grub, then grub will always use the latest kernel update as the default. You then have to change it manually.

---

### Post by Sparky222B on 2007-10-18
So there's no way to turn that off?

Also:

Ubuntu 7.10 / WinXP / OS X Intel

---

### Post by Jose Catre-Vandis on 2007-10-23
If you overwrite your mbr with the grub from your default boot partition, then kernal updates will for that install will be the ones that boot. From your last post, i am guessing that your default boot is not a linux install. Try using the bootloaders from either XP or OSX instead of grub?

---

### Post by r-mo on 2007-10-23
This is the important part of /boot/grub/menu.lst

```

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST

```

Make sure your windows / whatever boot entries go either before this line or after the ### END DEBIAN AUTOMAGIC KERNELS LIST later on.  Otherwise they're considered fair game.

---

### Post by Jose Catre-Vandis on 2007-10-23
found a bit more, try this

open up the menu.lst for your grub

[sudo gedit /pathtoyour/boot/grub/menu.lst[/code]

for your preferred default boot entry add
```
savedefault
``` as one of the lines

check all the other entries for this line and comment it out (usually the first one in the magic list)

then scroll up to the "Default" section and change "0" to "saved"  (no quotes)

Save out and reboot a couple of times.

---

