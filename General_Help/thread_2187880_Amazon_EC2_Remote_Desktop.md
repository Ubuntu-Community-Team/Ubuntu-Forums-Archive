---
title: "Amazon EC2 Remote Desktop"
date: 2013-11-14
forum: General Help
---

### Post by robmunfy2 on 2013-11-14
Hi,

I have an instance on Amazon EC2 of Ubuntu Server 13.10.

I am trying to install a desktop environment and get remote access to it. To do this, I've tried a couple of different things.

1) Use an ssh -x connection - Problem: Very slow indeed.
2) Install lxde and xrdp - Problem: Takes forever to build windows and (for example) draw the desktop background.
3) Install nomachine - Problem: NoMachine reports that there is no active display sessions.

Does anybody have any ideas how to either fix the above, or install something relatively fast on Ubuntu on EC2?

Thanks

---

### Post by Habitual on 2013-11-14
What size is the instance?

---

### Post by robmunfy2 on 2013-11-14
medium

---

