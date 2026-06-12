---
title: "remove grub"
date: 2017-04-22
forum: General Help
---

### Post by samerkinaan on 2017-04-22
hi,
i have ubuntu installed on my computer alongside windows, both are installed on separate ssds, my problem is when i disconnect the ssd with the ubuntu installed in, i cant start windows, the computer goes to bios settings, i can only start windows if i connect the ssd back.
normaly when i turn on my computer it opens a gnu grub version 2.02~beta2-36ubuntu3.2 and then i choose windows, how can i delete the grub and make my computer boot directly to windows (my goal is to work only with windows)

---

### Post by shridhar-kapshikar on 2017-04-22
Please have a look with similar kind of thread,
[https://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader](https://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader)

And let me know

---

### Post by samerkinaan on 2017-04-22
solved it
what i did was.

[LIST=1]
[*]Put the DVD in your optical drive and boot from it.

[*]Press a key when it displays Press any key to start from CD or DVD.

[*]Select your language etc. and click Next.

[*]Click Repair your computer.

[*]Click Troubleshoot.

[*]Click Advanced Options.

[*]Click automatic repair.

[/LIST]

---

### Post by donniecash on 2017-04-22
You might have had to set that drive as a bootable drive but I am glad that you have fixed the issue!

GRUB is a boot loader so it very possible that your drive with Ubuntu on it is also a bootable drive with the only bootloader(GRUB) on it

---

