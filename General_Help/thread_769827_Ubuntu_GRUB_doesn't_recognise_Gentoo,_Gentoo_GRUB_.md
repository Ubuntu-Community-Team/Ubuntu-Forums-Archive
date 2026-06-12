---
title: "Ubuntu GRUB doesn't recognise Gentoo, Gentoo GRUB doesn't recognise Ubuntu"
date: 2008-04-26
forum: General Help
---

### Post by Ender305 on 2008-04-26
I've had Ubuntu on my laptop for a while and I dicided to install gentoo on another partition.  When I installed Gentoo I installed the version of GRUB that came with it, next time I booted, I noticed that Ubuntu wasn't one of the choices, so I reinstalled the version of GRUB that came with my Ubuntu 7.10 live cd, and now, Gentoo doesn't show up.

What is wrong?

---

### Post by confused57 on 2008-04-26
> **Ender305 said:**
> I've had Ubuntu on my laptop for a while and I dicided to install gentoo on another partition.  When I installed Gentoo I installed the version of GRUB that came with it, next time I booted, I noticed that Ubuntu wasn't one of the choices, so I reinstalled the version of GRUB that came with my Ubuntu 7.10 live cd, and now, Gentoo doesn't show up.

What is wrong?
You'll need to add an entry to Ubuntu grub's menu.lst to boot Gentoo.  First you'll need to open a terminal(Applications---Accessories---Terminal) and check the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"
Once you've determined the Gentoo partition:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
Then add a configfile entry to the very end of your menu.lst to boot Gentoo, e.g.
```
title  Gentoo
configfile (hd0,2)/boot/grub/grub.conf
```

You'll need to substitute your Gentoo root for (hd0,2)...if your Gentoo partition is /dev/sda3, then (hd0,2) would work.../dev/sda4 would be (hd0,3), etc.

---

### Post by Ender305 on 2008-04-26
Don't I want to specify the root, kernel, and initrd?

---

### Post by confused57 on 2008-04-27
> **Ender305 said:**
> Don't I want to specify the root, kernel, and initrd?
With configfile booting you don't need to, see this guide:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

### Post by Ender305 on 2008-04-27
it worked, but grub doesn't show the menu at boot(unless you press ecs), is there a way to force the menu or change the default selection

---

### Post by confused57 on 2008-04-27
> **Ender305 said:**
> it worked, but grub doesn't show the menu at boot(unless you press ecs), is there a way to force the menu or change the default selection
Here's the best grub guide I know of:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
See the section on Hidden Menu and Timeout...

---

