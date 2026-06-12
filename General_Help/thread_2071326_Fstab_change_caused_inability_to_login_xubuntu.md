---
title: "Fstab change caused inability to login xubuntu"
date: 2012-10-15
forum: General Help
---

### Post by Thanduel on 2012-10-15
Hello

I've made a mess by changing my fstab; I was trying to move my home partition to sda7.   However the change failed and on restarting my machine I get to the login screen and it can't mount home, in fact all it does is refresh the login screen when I try to login.

I'm unable to edit fstab from vi in recovery mode.

Any help that avoids reinstalling would be greatly appreciated.

---

### Post by Cheesemill on 2012-10-15
> **Thanduel said:**
> I'm unable to edit fstab from vi in recovery mode.
What error are you getting?

You may need to first set the root filesystem to RW mode by doing:
```
mount -o rw,remount /
```

---

### Post by albandy on 2012-10-15
> **Thanduel said:**
> Hello

I've made a mess by changing my fstab; I was trying to move my home partition to sda7.   However the change failed and on restarting my machine I get to the login screen and it can't mount home, in fact all it does is refresh the login screen when I try to login.

I'm unable to edit fstab from vi in recovery mode.

Any help that avoids reinstalling would be greatly appreciated.

In the recovery menu, you've an option to remount in rw mode.
try selecting it and then use vim again.

---

### Post by Thanduel on 2012-10-15
Thank you for your responses, I've fixed it and found a decent guide to moving my home partition.

---

