---
title: "Dude, where's my XP? (Grub problem)"
date: 2006-09-15
forum: General Help
---

### Post by Dawnshadow on 2006-09-15
Yesterday night, I tried to boot into Windows XP for something and it wasn't in my Grub list. It was there yesterday afternoon, and I can see the partition Windows is on in Linux (actually, Ubuntu with KDE installed) so it's definetely there. I did fiddle with the order of OSes in a configuration file several weeks ago, but I can't think of anything else I might have done to trigger the disappearance of XP, especally not since I last used it. The option for the recovery console is still there (useless as it is to me) and all the Ubuntu listings, but... no XP....

---

### Post by Dawnshadow on 2006-09-15
...And restoring the original menu.lst worked. Win XP is on the menu again. I wonder what made it vanish...?

---

### Post by philippe_carlo on 2006-09-15
Make sure to have an entry like this in the file /boot/grub/menu.lst

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

Also, make sure to add this entry below the line
```

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by philippe_carlo on 2006-09-15
> **Dawnshadow said:**
> ...And restoring the original menu.lst worked. Win XP is on the menu again. I wonder what made it vanish...?

This morning's kernel update?

---

### Post by bruceliz on 2006-09-15
> **philippe_carlo said:**
> This morning's kernel update?

Almost certainly. It was the Sep. 14 kernel security update that overwrote my menu.lst, leaving all the Ubuntu entries (including a manually-entered one for a custom kernel) intact, but deleting all with the title

    Debian etch, kernel 2.6.16-2-[*]

---

### Post by Steveire on 2006-09-15
.

---

### Post by bulldog on 2006-09-15
> **Steveire said:**
> .
 I couldn't agree more :lol:

---

