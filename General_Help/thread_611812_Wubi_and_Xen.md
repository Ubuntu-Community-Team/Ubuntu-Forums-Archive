---
title: "Wubi and Xen"
date: 2007-11-13
forum: General Help
---

### Post by VanMuur on 2007-11-13
Hey everyone,

I was wondering if there was a Xen enabled Wubi kernel out there. I'd like to play with some domU's I've seen floating around, and I'm currently using a NTFS loop-mounted filesystem, installed by Wubi. I do know that there are some very specific Wubi related patches in the kernel, which I don't have the source to, so I can't rebuild the hybrid kernel myself. 

Ian

---

### Post by ago on 2007-11-13
Works like ordinary Ubuntu

---

### Post by VanMuur on 2007-11-13
So, if I install the ubuntu-xen-server pseudo-package, copy the resulting kernel over to /media/host/wubi/boot, modify my menu.lst file to use the new kernel, it will work no problem?

Ian

---

### Post by VanMuur on 2007-11-13
Ignore the part about copying the files, I just saw that /boot was linked to /media/host/wubi/boot, so its a moot point. But, the Xen kernel will work unchanged? I guess all the heavy lifting is in the initial RAM disk?

Ian

---

### Post by VanMuur on 2007-11-13
OK, I was able to get it working. When I installed ubuntu-xen-server, all I had to do was change (in Windows, not Ubuntu) the /boot/xen-* parameter to /wubi/boot/xen-*, and it booted successfully.

Thanks for the clarification.

Ian

---

### Post by Subhranshu on 2012-10-11
Hi All,

I have Installed xen-hypervisor-amd64 on Ubuntu 12.04 x86_64 wubi dual boot with win7,

sudo apt-get install xen-hypervisor-amd64
sudo sed -i 's/GRUB_DEFAULT=.*\+/GRUB_DEFAULT="Xen 4.1-amd64"/' /etc/default/grub
sudo update-grub
sudo sed -i 's/TOOLSTACK=.*\+/TOOLSTACK="xm"/' /etc/default/xen

Now the issue is that i am unable to boot with xen kernel,

I have tried lot of things like finding menu.lst in boot/grub in win7 but cant see it,

Please help me with this if possible,

Thanks

Subhranshu

---

### Post by bcbc on 2012-10-11
This thread is very old. There is no more grub-legacy with wubi so the comments above do not apply. I would advise creating a new thread instead.

---

