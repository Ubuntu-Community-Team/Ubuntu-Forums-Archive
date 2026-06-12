---
title: "[SOLVED] how to disable the timer in boot"
date: 2008-06-02
forum: General Help
---

### Post by mkrahmeh on 2008-06-02
hi
i have both vista and kubuntu on my PC, each time the boot starts the grub gives me the choices for the OS to boot, but there is a 10 seconds timer that in case i ddnt choose, the selected OS will boot automatically, how can i get rid of this?

thx

---

### Post by cmnorton on 2008-06-02
I believe if you add a "#" character in front of this line

timeout        3

in /boot/grub/menu.lst

the timeout will be disabled.

You'll need to edit the file as root (sudo /boot/grub/menu.lst), and I would back up the file first.

---

### Post by ibuclaw on 2008-06-02
I would recommend giving yourself a small gap to change OS.
```
timeout         2
```

And the uncommenting (removing the hash symbol) of this line would hide the boot menu too (Unless you press ESC).
```
hiddenmenu
```

Regards
Iain

---

### Post by mkrahmeh on 2008-06-04
thx guys
am taking a closer look at the file..am booting my pc like crazy trying things out..interesting :)

---

