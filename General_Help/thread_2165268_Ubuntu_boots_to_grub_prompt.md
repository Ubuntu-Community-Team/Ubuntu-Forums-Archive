---
title: "Ubuntu boots to grub prompt"
date: 2013-08-04
forum: General Help
---

### Post by Bkmz on 2013-08-04
Hi. I have installed Xubuntu 12.04. But now, I'm far away from this PC. 4000km, and it gets crazy.
Sometimes it show grub menu and boots normally, sometimes i need type 
```

set root=(hd1,1)
configfile /boot/grub/grub.cfg
```
is enough to show the grub menu.
But, sometimes I need to type following:
```
set root=(hd1,1)
linux /vmlinuz root=/dev/sda1
initrd /initrd.img
boot
```
And after it, PC may boot or not. I didn't see error messages, but some, that i realize is: > Kernel Panic. I could not find root device
Another error similar to initramfs, and i didn't get additional information about it.
And sometimes it boots...

I try 
```
update-grub
grub-install /dev/sda
```
And it don't help me...

Here are /etc/default/grub and /boot/grub/grub.cfg 
[https://gist.github.com/anonymous/6149967](https://gist.github.com/anonymous/6149967)

---

### Post by zteam2 on 2013-08-04
Hi there and welcome to Ubuntuforums :)

I would use Boot-repair to fix this issue.

Boot-Repair is a graphical tool, that can fix the most common GRUB-errors automatically.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It is available both as a LivCD and available to install with ppa from a your liveCD / liveusb-stick

---

### Post by Bkmz on 2013-08-06
How can I get debug log from grub2? And save in to HDD? 
Because, i haven't direct access to this computer. Only SSH.

---

### Post by Bkmz on 2013-08-06
After grub dpkg-reconfigure I also need's to type configfile /boot/grub/grub.cfg and only after that command i see grub menu, and can boot.
How to say grub loading grub.cfg automaticly?

---

### Post by zteam2 on 2013-08-06
Grub should load grub.cfg automatically if it doesn't then I guess it can't find the right path by itself which seems very strange.

I don't have very deep knowledge into grub myself, I usually just cheats around my problems by letting boot-repair do all the work for me. :-)

Anyway here is a link [https://help.ubuntu.com/community/Grub2/Troubleshooting#grub.3E-1](https://help.ubuntu.com/community/Grub2/Troubleshooting#grub.3E-1)

which can probablu provide some help.

---

