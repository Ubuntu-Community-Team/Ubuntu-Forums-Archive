---
title: "computer boots up in command prompt after running update manager"
date: 2008-05-27
forum: General Help
---

### Post by realbuntu on 2008-05-27
Hi,

After a successful run of update manager in ubuntu 8.04 lastnight. I rebooted the computer then but it boots up in a command prompt.  I can't remember exactly but it says something like busybox something and its a command prompt.

What do I do to get back into the login screen?

thanks for reading

---

### Post by cdtech on 2008-05-27
At the command prompt what do you get with:
runlevel

---

### Post by HoTMetaL on 2008-05-27
The same thing happened to me after running recommended Hardy updates. I found out that a (kernel 2.6.24-_17_) update modified */boot/grub/menu.lst* to a different one, so I Ctrl+Alt+Del at the BusyBox prompt to restart, 'Esc' to enter the grub menu, then select (kernel 2.6.24-**_16_** to boot.

Once back in gdm I used terminal to restore the original menu.lst:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.upg 
sudo cp /boot/grub/menu.lst~ /boot/grub/menu.lst
```

This worked for me. Good luck!

---

### Post by cdtech on 2008-05-27
My bad, thats the install CD you booted into (safe graphics mode or something). I just did the same thing looking at the CD.

Not much you can do in there, reboot without the CD.

---

### Post by danwood76 on 2008-05-27
The busybox terminal comes up when the initramfs is unable to load the kernel.
I would say there is an issue with Grubs menu.lst as already stated, choose the previous kernel, 2.6.24-16 to boot into your system.

Then post your menu.lst and and fdisk list.

```

cat /boot/grub/menu.lst # Dumps the menu.lst to terminal
sudo fdisk -l # Lists available partitions

```

---

### Post by realbuntu on 2008-05-27
thanks! its up and running!

---

### Post by simonsausages on 2008-05-27
I had the same issue with Ubuntu running as an install under Windows XP using WUBI. I tried the above fix by accessing the file in windows and editing it. It would not boot up under the old or new kernel. I had to reinstall in the end which lost all my previous work. Anyone had a similar issue under windows and fixed this without a reinstall?

---

