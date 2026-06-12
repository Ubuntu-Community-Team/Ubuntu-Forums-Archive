---
title: "Rebooting to Windows"
date: 2007-04-26
forum: General Help
---

### Post by kgx on 2007-04-26
I seem to remember Mandrake 9.x had an option to "Reboot to Windows". Is it possible in (K)ubunutu?

Basically, what I need is a way too to automatically reboot to windows (currently, ubuntu is default) without changing the grub menu.lst file. This means, after rebooting to windows, I can then reboot windows and go back to linux without evening touching the grub menu. This is quite handy when I need to remotely  reboot from linux to windows.

I think Mandrake used lilo but I certainly hope its possible with grub also.

Thanks in advance.

---

### Post by audax321 on 2007-04-27
Take a look here:

[http://ubuntuforums.org/showthread.php?t=382356h](http://ubuntuforums.org/showthread.php?t=382356h)

I posted a script there a while back you can use by passing it some arguments OR a simple solution is to make a shortcut to grub-reboot with some arguments to tell it what you want to boot into on the next reboot.

---

