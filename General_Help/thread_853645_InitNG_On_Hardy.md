---
title: "InitNG On Hardy?"
date: 2008-07-08
forum: General Help
---

### Post by ForksHolder on 2008-07-08
Hello,
I'm searching InitNG version for Hardy Ubuntu..
If it's ok, i'd like a Howto too :P


Thanks,
~ForksHolder

---

### Post by jpeddicord on 2008-07-08
Not an Apple question; moved to General Help.

---

### Post by ramjet_1953 on 2008-07-08
Why do you need InitNG?

> note: since Ubuntu 6.10 sysvinit has been replaced with upstart, which has similar features to InitNG, so InitNG is not needed

Here's a link discussing it:

[https://help.ubuntu.com/community/InitNG](https://help.ubuntu.com/community/InitNG)

Regards,
Roger :cool:

---

### Post by ForksHolder on 2008-07-09
Well, I've download the Hardy version and compiled.

When i did "sudo make check" it told me 3 of 17 tests were failled.
Then i did "sudo make install" and it done it.

Well, What now?

Thanks,
~ForksHolder.

P.S.
Sorry about the apple forum, my bad.

---

### Post by ForksHolder on 2008-07-11
Bump?

---

### Post by ForksHolder on 2008-07-14
Bump!!!!!!

---

### Post by timfelgentreff on 2008-07-31
Put "init=/sbin/initng" in the kernel-line of your menu.lst and try a reboot

---

