---
title: "Uh, no mouse"
date: 2005-05-18
forum: General Help
---

### Post by VincentP on 2005-05-18
I just installed Ubuntu 32-bit on my 64 bit machine.. because I don't want the hassle of all the 64 bit problems.  My mouse doesn't work.  I'm at the Ubuntu login, I can type in a username and password and log into the system, but the mouse just chills there, won't move, wont click.  Why?

---

### Post by Xian on 2005-05-18
There's a couple of quick possibilities:

1. The "InputDevice" section of your /etc/X11/xorg.conf file is incorrect.

- Reset X ($ sudo dpkg-reconfigure xserver-xorg) and input the mouse configuration manually (no autodetect). 

2. Your /boot/grub/menu.lst file contains an improper parameter in the "kernel" line.

- Include only 'ro' and reboot.

Example:

```
kernel    /boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro
```

---

