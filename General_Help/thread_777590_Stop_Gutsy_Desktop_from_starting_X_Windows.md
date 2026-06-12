---
title: "Stop Gutsy Desktop from starting X Windows"
date: 2008-05-01
forum: General Help
---

### Post by lukeburden on 2008-05-01
Hi all,

I've got a 7.10 desktop install that I want to run faster by not bothering with X Windows, and just booting straight to a terminal.

What configuration changes do I need to make to cause this to happen?

Thanks,

- Luke

---

### Post by warp99 on 2008-05-01
> **lukeburden said:**
> Hi all,

I've got a 7.10 desktop install that I want to run faster by not bothering with X Windows, and just booting straight to a terminal.

What configuration changes do I need to make to cause this to happen?

Thanks,

- Luke

Just remove the login manager:
```
sudo apt-get remove gdm
```
now when you need a desktop just login to a terminal and type 'startx'. Now apt-get may ask to remove the package ubuntu-desktop, but this is only for the meta package not the actual desktop. Also the configuration files for gdm are still on your system in-case you want to re-install the login manager at a later date.

---

