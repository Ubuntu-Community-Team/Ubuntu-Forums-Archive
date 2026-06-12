---
title: "howto eliminate all those getty in edgy?"
date: 2006-10-31
forum: General Help
---

### Post by elettronicha on 2006-10-31
```
$ ps aux|grep getty
root      3788  0.0  0.0   1600   508 tty1     Ss+  12:04   0:00 /sbin/getty 384
root      3789  0.0  0.0   1596   504 tty2     Ss+  12:04   0:00 /sbin/getty 384
root      3790  0.0  0.0   1600   508 tty3     Ss+  12:04   0:00 /sbin/getty 384
root      3791  0.0  0.0   1600   508 tty4     Ss+  12:04   0:00 /sbin/getty 384
root      3792  0.0  0.0   1596   504 tty5     Ss+  12:04   0:00 /sbin/getty 384
root      3793  0.0  0.0   1600   508 tty6     Ss+  12:04   0:00 /sbin/getty 384
```

I have 6 getty terminals running and want just one. Up to Dapper eliminating them was simple by editing /etc/inittab.

Now with Edgy /etc/inittab disappeared (I suppose because of the new init system upstart).

---

### Post by jordilin on 2006-10-31
This was submitted as a bug. The solution is here:
[https://launchpad.net/distros/ubuntu/+source/upstart/+bug/61539](https://launchpad.net/distros/ubuntu/+source/upstart/+bug/61539)

---

### Post by elettronicha on 2006-10-31
Ok, I missed it, though tried a search here and at malone. Thanks, amigò català.:D

---

### Post by yopnono on 2006-10-31
Question. All those getty, they are not needed or?
You normally only need 1 and 7 right?
Or only 7.

---

### Post by elettronicha on 2006-10-31
> **yopnono said:**
> All those getty, they are not needed or?
You normally only need 1 and 7 right?

Depending on your needs. In general sys-admins need to have many running getty terminals and switch among them with ctrl+alt+Fx. I, as desktop user, don't need nothing more but F7 and F1 (in very very few cases).

---

### Post by yopnono on 2006-10-31
ok thanks

---

