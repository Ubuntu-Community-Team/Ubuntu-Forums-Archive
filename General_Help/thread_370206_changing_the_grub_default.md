---
title: "changing the grub default"
date: 2007-02-25
forum: General Help
---

### Post by H-Radical on 2007-02-25
Hi all,

I was wondering, how can I change the default option on grub? I just recently upgraded to kernel 2.6.17-11, which is causing me problems... but I can't figure out how to change the grub default so that it automatically boots into 2.6.17-10.

Any help is appreciated.
Thanks.

---

### Post by taurus on 2007-02-25
You can change the boot default from 0 to whatever the entry for the old kernel (remember, Linux starts counting from 0 so the first entry is 0, the second entry is 1, etc.) in /boot/grub/menu.lst.  

```
gksudo gedit /boot/grub/menu.lst
```

---

