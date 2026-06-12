---
title: "[SOLVED] trying to enter level 3"
date: 2006-12-09
forum: General Help
---

### Post by nga911 on 2006-12-09
am using Ubuntu 6.10 and am trying to enter level 3 . but i don't know how ](*,) ](*,) can some body help me ..... i also want to install the kernel sources were can i get them.:confused: thanks in advanc

---

### Post by Wim Sturkenboom on 2006-12-09
edit /etc/inittab and change the initdefault to 3
reboot machine
```
# The default runlevel.
id:[COLOR="Red"]**2**[/COLOR]:initdefault:
```

---

### Post by steve.horsley on 2006-12-09
To change to runlevel 3 use the command **sudo init 3** but you won't see anything happen because all levels are configured to run the same services. What are you actually trying to do?

Use synaptic and search for "linux". I can't remember the exact packages. If you're doing compiling, you will also want to install package "build-essential".

---

