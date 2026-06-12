---
title: "Redisabling root"
date: 2005-04-24
forum: General Help
---

### Post by macmasterxiv on 2005-04-24
I've enabled the root account for something I needed to do, but I'd like to revert it back to its default disabled state. Is there a way to do this?

---

### Post by mendicant on 2005-04-24
I suppose you could try removing the password from /etc/shadow.

---

### Post by stevetone on 2005-04-25
I wouldn't edit the password file directly. Instead, use the command

sudo passwd -l root

There is a good writeup on this [here](http://www.ubuntulinux.org/wiki/RootSudo)

---

