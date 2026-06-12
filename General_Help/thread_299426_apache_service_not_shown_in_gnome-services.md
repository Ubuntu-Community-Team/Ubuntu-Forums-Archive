---
title: "apache service not shown in gnome-services"
date: 2006-11-14
forum: General Help
---

### Post by suoko on 2006-11-14
Hi,

I have a problem with both an edgy fresh install and an dapper->edgy upgrade.

In gnome services apache is not shown, therefore I can't enable/disable it to be loaded at startup.

Is this a bug?

---

### Post by mayonaise15 on 2006-11-14
If you put this code into a terminal window, does it come back with anything?

```
sudo ps -A | grep 'apache'
```

---

### Post by suoko on 2006-11-14
Yes.

I usually use /etc/init.d scripts to start/stop it.

I tried removing apache with purge and reinstall it with no success.

---

### Post by mayonaise15 on 2006-11-14
I don't know if apache not showing up in the gnome services is a bug or not, but I found [this article]("http://linuxhelp.blogspot.com/2006/04/enabling-and-disabling-services-during_01.html") that may be of some help to you.

Scroll down to to Debian method section.

---

### Post by suoko on 2006-11-16
I installed edgy on a third PC and again: no apache service in gnome services.

This is likely a bug

---

### Post by suoko on 2006-11-17
I reported this to gnome as a bug.

---

