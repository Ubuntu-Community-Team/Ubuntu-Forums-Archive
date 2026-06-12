---
title: "No premission to boot??"
date: 2007-12-20
forum: General Help
---

### Post by Dark Aspect on 2007-12-20
I can't boot off my hard drive anymore,I get a error saying I don't have permission to access to GDM and that log in is not possible........I think I may have messed up my Ubuntu installation by logging in as a root and changing some permissions - I know that was dumb.Is there anyway at all to save my system I tried booting of a live CD to change the permission to every thing as a root which got me to the log in screen but I still can't log in.I have tons of data I might lose if I have to reinstall,ideas?

Failsafe gnome fails too.........

---

### Post by cdenley on 2007-12-20
If the permissions are wrong on gdm, try reinstalling it.
```

sudo aptitude reinstall gdm

```

If you changed permissions on your entire filesystem, then I think you should reinstall the entire system.

---

### Post by Dark Aspect on 2007-12-20
> **cdenley said:**
> f you changed permissions on your entire filesystem, then I think you should reinstall the entire system.
Yes........I did for some insane reason.I did however play around with the live CD and get my system to boot up again....I think its ok now but whats the default permission for the stuff in the root?Now it seems I have access to folder like /bin and /usr just as a stranded user.Would fsck fix this?

---

### Post by rsambuca on 2007-12-20
fsck won't fix this type of problem.  Unless you know exactly which folders and files you tampered with, I would suggest a fresh install as well.  Otherwise, it is likely you will keep running into errors as programs can't access necessary folders and files.

---

