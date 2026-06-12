---
title: "How to get the splash back while booting?"
date: 2007-03-23
forum: General Help
---

### Post by Jochus on 2007-03-23
I'm using Xen on my desktop PC, so I had to configure a Xen kernel:

```

title Xen 3.0 / XenLinux 2.6
root (hd0,0)
kernel /boot/xen-3.gz
module /boot/vmlinuz-2.6.16.29-xen root=/dev/sda1 ro quiet splash
module /boot/initrd.img-2.6.16.29-xen
savedefault
boot

```

The problem is now I can't see the Ubuntu splash while booting (like : Bringing up network ...). The screen stays black. Once I'm at the login window, I have my screen back ...

A normal kernel look in menu.list like this

```

title           Ubuntu, kernel 2.6.15-28-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

```

So I can't see exactly what I misconfigured?

---

### Post by swamytk on 2007-03-23
While building initrd for xen kernel, enable splash

---

### Post by Jochus on 2007-03-28
Can you explain me how to enable it?

I've builded the initrd like this:

```
mkinitramfs -o initrd.img-2.6.16-xen 2.6.16-xen
```

But how to enable splash?

---

