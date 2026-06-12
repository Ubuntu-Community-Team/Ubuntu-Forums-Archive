---
title: "crc error - Kernel Panic - not syncing"
date: 2008-05-06
forum: General Help
---

### Post by neburzaragoza on 2008-05-06
Hi there,

when I turned on my computer the other day, after a freeze and a manual reboot i found the next fatal message

```
starting up...
[29.169107] crc error
[29.169946] Kernel Panic - not syncing: VFS: unable to mount root fs on unknown-blocks(0,0)
```

some clues:

1- I didn't change my /boot
2- nor my menu.lst
3- it just appeared after a manual reboot

any idea or suggestion will be appreciate.

thanks and cheers

---

### Post by neburzaragoza on 2008-05-08
any idea?

---

### Post by ShelJ on 2008-05-09
I ran into this problem after my weekly updates last week. I've reported it here: [HTML]https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/226356[/HTML]

You may find something helpful, in the replies.  AS for me I'm reverting back to kernel 2.6.24-16, as it seems to be the one that works best for my needs at the moment.

I hope that this helps give you an idea of where to go from here.

---

