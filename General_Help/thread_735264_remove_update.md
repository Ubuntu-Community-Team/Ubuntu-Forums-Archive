---
title: "remove update"
date: 2008-03-25
forum: General Help
---

### Post by marco45 on 2008-03-25
hi, this afternoon I installed update for my sound card, I don,t know the name of this install :(, since this install, I only heard sound by my right speaker and I want to remove this update,

I use ubuntu 7.10

thank you

---

### Post by cdenley on 2008-03-25
You can't really do much without a package name.
```

sudo gedit /var/log/apt/term.log
ls -l /var/cache/apt/archives|grep 2008-03-21

```

---

### Post by marco45 on 2008-03-27
Thank you

---

