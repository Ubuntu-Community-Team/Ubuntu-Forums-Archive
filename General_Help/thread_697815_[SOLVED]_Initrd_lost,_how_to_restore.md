---
title: "[SOLVED] Initrd lost, how to restore?"
date: 2008-02-15
forum: General Help
---

### Post by ayampanggang on 2008-02-15
OK so i messed up. Tried to get a bit of space on my tiny 30mb /boot but ended up deleting initrd.img accidentally.

now my approach to fix it is to chroot from a Damn Small liveCD into my Gutsy environment, and do some make && make menuconfig to rebuild the kernel.

the problem is that i can't chroot. tried to do
```

chroot /mnt/hda3 /bin/bash

```
it gave me this error:
FATAL: kernel too old.

turns out that the Damn Small liveCD uses 2.4 kernel.

I'm not that new to linux but i haven't really done any troubleshooting either. Particularly i never chroot aside from installing gentoo couple years ago so i dont know much about it.

Can anyone tell me how to chroot from my damn small livecd into my ubuntu gutsy environment?
Or are there better methods to recreate my lost initrd.img?

Thank you so much!

---

### Post by pointone on 2008-02-15
You should be able to chroot fine from the Ubuntu live CD and simply run "update-initrd" to regenerate the image.

---

### Post by deepclutch on 2008-02-15
@OP:
boot with ubuntu cd or any 2. 6 kernel livecd.
mount ur partition(ubuntu hdd),
chroot as below(guessing /mnt as mount dir)
```

mount -t proc proc /mnt/proc
__
mount --bind /dev     /mnt/dev
__
chroot  /mnt    /bin/bash


```
now,do as below:
```

apt-get install --reinstall linux-image-(version).
---
or 
dpkg-reconfigure linux-image-(version)



```
that will do

---

### Post by ayampanggang on 2008-02-17
thanks i just used a 2.6 kernel cd and it worked wonders :D
never thought different kernel version gives problems

---

