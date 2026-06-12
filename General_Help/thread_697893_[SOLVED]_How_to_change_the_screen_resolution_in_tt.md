---
title: "[SOLVED] How to change the screen resolution in tty1...tty6"
date: 2008-02-15
forum: General Help
---

### Post by b0rka7a on 2008-02-15
How ? It's now working @ 640x480 (default). I want it @ 1024x768. I tried with adding vga=791 in grub's menu.lst, but then didn't have any fonts at all in the terminals.
Anyone can help me with that ? Thanks in advance ;)

---

### Post by Anduu on 2008-02-16
This might pertain to your problem....

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910)

There are some suggested fixes there as well.

---

### Post by b0rka7a on 2008-02-16
Thank you for the link.
I added "vga=791", and removed "splash" and "quiet".
It's @1024x768 now :)

Edit: It's working @60Hz. Could it run @85Hz ? :D

---

### Post by b0rka7a on 2008-02-16
Also I saw SUSE 10.3 today and the terminals (tty1...tty6) were with wallpaper. Can I set any wallpaper on mine too ?

---

