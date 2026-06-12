---
title: "How do I delete hibernate data"
date: 2013-01-14
forum: General Help
---

### Post by kevpatts on 2013-01-14
I accidentally hibernated XFCE on Friday when leaving work. Now every time I log in all my previous apllications from that hibernation load up, even if I close them and log out.

Not even that but there are no title bars on anything and I can't change windows, move windows, maximise/minimise, use shortcuts or really use my PC at all any more.

How do I delete the hibernation data and startup normally? I've already tried "noresume" kernel param, "swapoff-a; mkswap /dev/sda1; mkswap /dev/sdb1; update-initramfs -u" and I've editted /etc/fstab to explicitly state those partitions as the swap partitions, but no effect so far.

---

### Post by Elfy on 2013-01-14
Try running 

```
xfwm4
```

to get the window manager running again.

In System Settings - Session and Startup - Session tab

Clear saved sessions.

---

### Post by kevpatts on 2013-01-14
Clearing the sessions did the trick, thanks a lot Elfy.

---

