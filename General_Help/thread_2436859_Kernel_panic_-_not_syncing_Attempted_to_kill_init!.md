---
title: "Kernel panic - not syncing: Attempted to kill init! exitcode=0x00007f00"
date: 2020-02-14
forum: General Help
---

### Post by z3132 on 2020-02-14
Good afternoon,

I am encountering the following error when trying to boot Ubuntu:

```
Kernel panic - not syncing: Attempted to kill init! exitcode=0x00007f00
```

It initially required a manual fsck, but after performing it and restarting, I get the message above, none of the kernels can be booted, not even recovery, full pic:

[https://i.imgur.com/kjMJvWR.jpg](https://i.imgur.com/kjMJvWR.jpg)

I am running out of ideas, what went wrong and how can I recover it please?

Thanks a lot.

---

### Post by Bashing-om on 2020-02-14
z3132; Hello - Welcome to the forum 

Hardware issues ?

What results when you boot up a liveUSB/DVD ?

If good in the live environment - well maybe next is to look at the boot code on the hard drive.

[INDENT][INDENT]gots to be a reason
[/INDENT][/INDENT]

---

### Post by z3132 on 2020-02-17
Booting from liveusb works fine. How can I do that and cannot the kernel be repaired using chroot?

---

### Post by vidtek on 2020-02-17
> **z3132 said:**
> Booting from liveusb works fine. How can I do that and cannot the kernel be repaired using chroot?

Check this out if you can't get boot-repair to work.....[https://ubuntuforums.org/showthread.php?t=2436958&p=13932625#post13932625]("https://ubuntuforums.org/showthread.php?t=2436958&p=13932625#post13932625")

Tony.

---

