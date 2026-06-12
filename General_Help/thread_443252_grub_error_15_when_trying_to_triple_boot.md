---
title: "grub error 15 when trying to triple boot"
date: 2007-05-14
forum: General Help
---

### Post by el_ricardo on 2007-05-14
hello all! I'm trying to triple boot debian, windows, and ubuntu studio. Debian and windows were already on my disk when i came to install ubuntu, so during the installation i opted not to install GRUB, and update my grub configuration so it would look in the correct place. In my case, I used an entire 400GB SATA disk (/dev/sdb) in my grub config files this equates to hd2. So i added these lines to my menu.lst:

```

title           ubuntu studio
root            (hd2,0)
kernel          /vmlinuz root=/dev/sdb1 ro
initrd          /initrd.img

```

^these are all pointing to the correct locations as far as i am aware, the kernel and initrd are in those places on /dev/sdb1

and my device.map looks like this:

```

(hd0)	/dev/hdb
(hd1)	/dev/sda
(hd2)	/dev/sdb

```

debian is installed to /dev/sda, and windows is on /dev/hdb1 if this makes a difference

cheers!

---

### Post by psusi on 2007-05-14
Try pointing it to the actual specific kernel and initrd instead of the generic vmlinuz symbolic link.

---

