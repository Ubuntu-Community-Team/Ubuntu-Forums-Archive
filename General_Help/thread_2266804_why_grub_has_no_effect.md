---
title: "why grub has no effect"
date: 2015-02-25
forum: General Help
---

### Post by M_Hao on 2015-02-25
I have Ubuntu 14.04LTS dual boot with xp. most of the time I use Ubuntu. So I set grud time out to 3 or even 0. save and update. but when I reboot. it still count 10sec before auto log in Ubuntu. I change hidden time out quiet to false. It is the same. It seems everything I did with grub has no effect.  Why is that? I did check and sure it was changed afterward.

---

### Post by Bucky Ball on 2015-02-25
After you make the change (in /etc/default/grub), are you then saving and closing the file and:

```
sudo update-grub
```

Without issuing that command after saving the file, changes will be lost.

---

### Post by M_Hao on 2015-02-25
Yes, I did that and checked it and sure it was updated.

---

### Post by deadflowr on 2015-02-25
When you ran update-grub, did you see this warning
> Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Is GRUB_HIDDEN_TIMEOUT set?

---

### Post by M_Hao on 2015-02-25
it is set to 0

---

