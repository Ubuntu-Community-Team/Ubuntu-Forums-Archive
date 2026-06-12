---
title: "Ubuntu startup lockup after repartitioning"
date: 2007-05-30
forum: General Help
---

### Post by Wutzl on 2007-05-30
I repartitioned my harddisk (resizing partitions, switching Ubuntu partition from extended to primary, creating separate /home partition).

I booted Knoppix, edited the grub configuration, reinstalled Grub and adjusted fstab.

Now I have the Grub menu back and can boot into Windows Vista. When I tell Grub to boot Ubuntu, I get no error and the Ubuntu startup screen appears. But the progress bar remains stuck and the caps lock and pad lock (?) lights start blinking. After several minutes, a Busybox prompt appears - but I have no idea what to do there.

Anyone has an idea what goes wrong here? How can I hide the Ubuntu startup screen so I know where during startup the critical error occurs?

Thanks!

Chris

---

### Post by merlinus on 2007-05-30
You can remove quiet and splash from the kernel line in /boot/grub/menu.lst.

Good luck!

-merlin

---

### Post by Crafty Kisses on 2007-05-30
> **Wutzl said:**
> I repartitioned my harddisk (resizing partitions, switching Ubuntu partition from extended to primary, creating separate /home partition).

I booted Knoppix, edited the grub configuration, reinstalled Grub and adjusted fstab.

Now I have the Grub menu back and can boot into Windows Vista. When I tell Grub to boot Ubuntu, I get no error and the Ubuntu startup screen appears. But the progress bar remains stuck and the caps lock and pad lock (?) lights start blinking. After several minutes, a Busybox prompt appears - but I have no idea what to do there.

Anyone has an idea what goes wrong here? How can I hide the Ubuntu startup screen so I know where during startup the critical error occurs?

Thanks!

Chris

Hey hows it going, you should try booting in verbose mode at the boot screen.
```
Ctrl+Alt+F2
```

---

### Post by Wutzl on 2007-05-30
thanks for the hints. In the end, Ctl-Alt-F1 did the trick for me and displayed the error message. Turns out the UUID of my linux partition had changed so I had to update the kerneloptions in my grub configuration.
Guess I will be switching from adressing disks by UUID to adressing them by LABEL.

---

