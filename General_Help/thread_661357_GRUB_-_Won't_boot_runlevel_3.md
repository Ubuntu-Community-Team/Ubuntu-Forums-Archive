---
title: "GRUB - Won't boot runlevel 3"
date: 2008-01-07
forum: General Help
---

### Post by sprucio on 2008-01-07
When I choose the text mode, it keeps booting into runlevel 2. I check this by running 'who -r'.

Can anyone tell me what's causing it to do this?

Looking at my grub.conf (/boot/grub/menu.lst) file:
```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=d260c5d1-e0de-4a41-8b56-de6cb041e1fb ro 
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (text mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=d260c5d1-e0de-4a41-8b56-de6cb041e1fb ro 3 
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=d260c5d1-e0de-4a41-8b56-de6cb041e1fb ro single
initrd          /boot/initrd.img-2.6.22-14-generic
```

---

### Post by dcstar on 2008-01-08
> **sprucio said:**
> When I choose the text mode, it keeps booting into runlevel 2. I check this by running 'who -r'.

Can anyone tell me what's causing it to do this?
.........

Runlevel 2 is what Ubuntu boots into no matter what you select.

---

### Post by sprucio on 2008-01-09
I have three entries within in that grub.conf file. If I choose the last entry, it boots into single mode perfectly.

I used to be able to do this on older versions of Ubuntu. Is there any chance that upstart is modifying this behavior?

---

### Post by heindsight on 2008-01-09
There is a bug report about this on launchpad: [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/85014](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/85014)

For now it seems there's not much that can be done about it, except trying to hack the rc-default
script and hoping it works without breaking things.

---

