---
title: "bind9chmod Operation not permitted"
date: 2014-10-18
forum: General Help
---

### Post by peridian on 2014-10-18
Hi,

Was following this tutorial on how to migrate a bind9 installation to a chroot jail: [http://www.faqforge.com/linux/install-bind-nameserver-in-a-chroot-on-debian-6/](http://www.faqforge.com/linux/install-bind-nameserver-in-a-chroot-on-debian-6/)

Followed it step by step, but when I ran /etc/init.d/bind9 start, I got:

bind9chmod: changing permissions of '/var/run/named': Operation not permitted

I am assuming that the -t {chroot-path} option in the /etc/defaults script has worked, and it is actually looking for /{chroot-path}/var/run/named, which I have created and set the owner as bind:bind on (in fact the entire {chroot-path} is owned by bind:bind with 755 permissions).

What have I missed?  Any help appreciated.

Regards,
Rob.

---

### Post by peridian on 2014-10-18
Okay, nevermind, I don't know what was going on, but all of a sudden this has started working as expected.

Maybe I missed out sudo on the bind9 start or something.

Rob.

---

