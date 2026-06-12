---
title: "Can't update"
date: 2008-06-18
forum: General Help
---

### Post by stealthsniper96 on 2008-06-18
Hi. I tried to update ubuntu today (8.04) and I get this error.
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache->open() failed, please report
```

I also got it when trying to update java. So I ran "dpkg --configure -a" in terminal and it gave me
```
dpkg: requested operation requires superuser privilege
```

What do I do? Sorry I'm new to linux.

---

### Post by YaroMan86 on 2008-06-18
> **stealthsniper96 said:**
> Hi. I tried to update ubuntu today (8.04) and I get this error.
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache->open() failed, please report
```

I also got it when trying to update java. So I ran "dpkg --configure -a" in terminal and it gave me
```
dpkg: requested operation requires superuser privilege
```

What do I do? Sorry I'm new to linux.

You need to do this code:

```
sudo dpkg --configure -a
```

For future reference, whenever a program errors out, talking about permissions or privilieges or something of similar meaning, use sudo to elevate to root for the command.

---

