---
title: "[SOLVED] GRUB problem"
date: 2008-02-12
forum: General Help
---

### Post by silentabe939 on 2008-02-12
Okay so I was dual booting Ubuntu and Debian. While working in Ubuntu i purposely deleted the Debian partition.  Since this was the main boot GRUB now when i boot up tries to load then just says "Error 15." I know this is my fault and was just hoping to fix this problem without just reinstalling Ubuntu. Any ideas.

I have also learned that linux is like a DM. When it says "Are you sure you wanna do that?" you better be dang sure you know what your doing, otherwise the consequenses will be dire.

---

### Post by apetresc on 2008-02-12
Error 15 implies that the partitions are alright, but it can't find the actual boot image or kernel. Can you post the relevant entry from menu.lst?

---

### Post by silentabe939 on 2008-02-12
I may be able to do that, how would I?

---

### Post by apetresc on 2008-02-12
```
gedit /boot/grub/menu.lst
``` Copy and paste that here.

---

### Post by iris-n on 2008-02-12
And by doing that you deleted the partition that had the boot information. For me, the solution was to reinstall grub. This can be done in a plethora of ways, i think the easiest would be using the [SuperGrub]("http://supergrub.forjamari.linex.org/?section=documentation")  disk.

---

### Post by mrsteveman1 on 2008-02-12
Boot an ubuntu CD and run this:
```

sudo grub
find /boot/grub/stage1 (take note of the numbers, use the ones find gives you NOT mine)
root (hd0,0)
setup (hd0,0)
```

This will check the partition linux is supposed to be on and tell you where it is (in bios numbering), then you can tell grub to root itself from this partition (so it knows where to get its files), then install grub to the linux partition boot sector.

This should fix grub.

---

### Post by silentabe939 on 2008-02-12
Okay the super grub cd was able to fix the problem, if only i new how. thanks guys.

---

### Post by Shyper on 2008-02-12
SuperGRUB is like magic. I accidentally screwed up my GRUB installation once; five keypresses with SuperGRUB later, I was able to boot again. Amazing.

---

