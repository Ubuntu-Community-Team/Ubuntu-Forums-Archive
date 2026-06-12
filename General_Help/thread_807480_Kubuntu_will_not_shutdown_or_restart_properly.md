---
title: "Kubuntu will not shutdown or restart properly"
date: 2008-05-25
forum: General Help
---

### Post by Keith.Anyan on 2008-05-25
I upgraded to Kubuntu 8.04 and now I'm unable to shutdown or restart properly.  Each time I shutdown or restart it just goes to a black screen and sits there until I either press the restart or power button.

---

### Post by cariboo on 2008-05-25
Open a terminal and type

```
sudo halt
```

To shutdown the system and see what happens.

If you want to restart, in a terminal type

```
sudo reboot
```

Good Luck

Jim

---

### Post by pixel :-) on 2008-05-25
You have fglrx(ATI driver)?Theres a bug here the fix[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/118605/comments/32]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/118605/comments/32")

the ctrl+ald+del should still work,it's doing a soft shutdown.

---

