---
title: "Run-Level in Ubuntu"
date: 2008-01-28
forum: General Help
---

### Post by Paris Heng on 2008-01-28
Dear all,

I have changed the run-level of boot up using the following configuration,

#/etc/event.d/rc-default ------> telinit 1

When I boot, i go into the prompt login, my problems is, if i want to change back to GNOME, how ya? Just type startx?

Please assist.

---

### Post by CheShA on 2008-01-28
```
/etc/init.d/gdm start 
```

or better still 
```
telinit 2
```

---

### Post by pointone on 2008-01-28
Runlevel 1 is also known as single user mode, and is intended primarily for troubleshooting and debug purposes. It logs you in as root and loads only essential services. Unless this is what you intended, you should not use runlevel 1. If you only want a command prompt, use runlevel 2 and stop gdm from loading on startup.

---

