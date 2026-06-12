---
title: "LVPM issues"
date: 2008-06-16
forum: General Help
---

### Post by martine.ginette on 2008-06-16
Hi all,

I have used this beautiful LVPM program to transfer my WUBI installation to a faster one. Everything is perfect until I restart the computer and boot on the new partition: UBUNTU crash before the log page with a lot of error about not having the rights to write on files, about /var, about many other things...

Someone? An idea?

Many thanks,
Martin.

---

### Post by martine.ginette on 2008-06-19
Got it!

LVPM does not check if the destination partition is big enough to receive the old installation...

In my case it was not the case, and LVPM did not say anything...

hehe

Can someone fix this?

Thanks guys for your work!

Martin.

---

### Post by martine.ginette on 2008-06-19
By the way, I tried to transfer the installation a second time, and it created big problems: after a reboot, grub did not even wanted to start!

So: LiveCD and brand new installation on the new partition......

Let's try a new transfer to a bigger partition...

Martin.

---

### Post by ago on 2008-06-19
I wrote a couple of scripts you can also use as an alternative to LVPM

[https://wiki.ubuntu.com/WubiGuide#head-410d166b798499e97402b5010a969c2d7d0ca6da](https://wiki.ubuntu.com/WubiGuide#head-410d166b798499e97402b5010a969c2d7d0ca6da)

---

