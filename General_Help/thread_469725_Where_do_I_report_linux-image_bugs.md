---
title: "Where do I report linux-image bugs?"
date: 2007-06-10
forum: General Help
---

### Post by javaJake on 2007-06-10
I got this error while linux-image-2.6.20-16-generic was installing/upgrading:

```
Unpacking replacement linux-image-2.6.20-16-generic ...
Running postrm hook script /sbin/update-grub
You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!
```

I want to report this as a bug (low severity, obviously), but I don't know where. Launchpad doesn't have anything but linux-kernel-generic as far as Linux kernel stuff goes.

---

### Post by tpg on 2007-06-10
I'd file it against the linux kernel package on launchpad, and just say in the bug description that it actually applies to the kernel image package.

---

### Post by javaJake on 2007-06-10
Heh, then file a wishlist bug against Launchpad for not having linux-image I suppose. :D

---

### Post by bapoumba on 2007-06-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/78552](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/78552) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				And also:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106264]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106264")

---

### Post by javaJake on 2007-06-12
Ah, thanks for doing that! I forgot to. :)

**Edit** Oh, looks like those are someone else's bug reports. Why can't I ever find other's bug reports? Ugh.

---

