---
title: "need to replace files in /usr/share, help plz"
date: 2007-03-24
forum: General Help
---

### Post by mreiland on 2007-03-24
I won't bother everyone with the details of how I could do such a silly thing such as deleting the following directories, but it happened and I would love to know how to rectify the situation.


I've deleted /usr/share/postgresql & /usr/share/postgresql-common, making it impossible to install/uninstall postgresql-8.1.

Any hints?

Thanks
Michael

---

### Post by Waappu on 2007-03-24
Hi

Can you re-install it ?
```
sudo aptitude reinstall postgresql-8.1
```

---

### Post by raja on 2007-03-24
Is it in your trash - then you can restore it.

---

### Post by mreiland on 2007-03-24
nope, reinstall gives me the same error and I deleted with good ole rm :(


I tried the edit->fix broken packages as suggested in another thread and that didn't work either.

The problem is that it's looking for scripts in these directories and borks when it doesn't find them.

---

### Post by mreiland on 2007-03-25
Oh well I went ahead and reinstalled.  You live and you learn :)

---

