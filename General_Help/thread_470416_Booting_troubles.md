---
title: "Booting troubles"
date: 2007-06-11
forum: General Help
---

### Post by BloodyClownSuit on 2007-06-11
This morning I got up and installed the new updates...i think they were linux-headers i can't really remember. anyways, after the restart, my computer just hangs when it tries to boot from the hard disk. no "starting grub" message or anything.

the live cd is working and i fsck'd the boot partition which was clean...

any ideas? because i'm pretty stumped 
thanks in advance.

---

### Post by reidms on 2007-06-11
So- you can not even get to grub to select recovery mode?

---

### Post by BloodyClownSuit on 2007-06-11
right...

i boot from cd first so i see that it looks for things to boot off of my cd-drives then it hangs (no response from keyboard) after that.

I also switched the boot order and it did the same thing just without the cd messages

im thinking just set up grub manually? i did it once or twice in gentoo... but its been a while
im guessing its an MBR problem

---

### Post by BloodyClownSuit on 2007-06-11
nm i do have keyboard

---

### Post by BloodyClownSuit on 2007-06-11
yeah that was the problem i guess
```
grub-install /dev/hda
```
did the trick.

---

