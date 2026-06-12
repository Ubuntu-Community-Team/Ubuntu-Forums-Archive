---
title: "Where did the good old intttab go?"
date: 2007-02-16
forum: General Help
---

### Post by ubix on 2007-02-16
Does anybody know where to find the documentation for the new Ubuntu's **init** process. I was very disappointed to find out that even in newly released Ubuntu Linux books there is no mention of now missing **inittab**.

---

### Post by llamakc on 2007-02-16
Upstart is now used. Look in /etc/event.d

---

### Post by ubix on 2007-02-16
> **llamakc said:**
> Upstart is now used. Look in /etc/event.dI have figured out that much. What about the documentation?

---

### Post by llamakc on 2007-02-16
cd /usr/share/doc/upstart && zcat README.Debian.gz |less

---

### Post by ubix on 2007-02-16
Thanks :)

---

### Post by pn8830 on 2007-03-10
> **llamakc said:**
> cd /usr/share/doc/upstart && zcat README.Debian.gz |less

This is interesting. I did exactly what you suggested. Here is what I found in the doc you are referring to:

> How do I change the default runlevel?
-------------------------------------

Edit the /etc/inittab file, if you installed edgy fresh you'll need to
create it.  Locate, or write, the following line:

    id:N:initdefault:

Where N is the default runlevel, change this to match.


So this document assumes that /etc/inittab exists. But still there is no /etc/inittab on my system. :(

---

### Post by pointone on 2007-03-20
Ummm...

How do I change the default runlevel?
-------------------------------------

Edit the /etc/inittab file, [B][U]if you installed edgy fresh you'll need to
create it[/U][/B]. Locate, or write, the following line:

id:N:initdefault:

Where N is the default runlevel, change this to match.

:)

---

