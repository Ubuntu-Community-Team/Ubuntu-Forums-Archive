---
title: "lost /home, need to add a new user"
date: 2006-11-14
forum: General Help
---

### Post by yurtfg89327tfg0o on 2006-11-14
Whilst trying to get wine running on Kubuntu 6.10 amd64 I have lost my /home dir.
Is it possible (and if so how) to create a user account that will set up a new user directory structure and default settings, like when you first install Kubuntu?
Or do I have to reinstall from scratch again?

---

### Post by taurus on 2006-11-14
You mean /home is gone completely!!!  Yes, you can create a new user again...  Boot into recovery mode and at the prompt, do

```
useradd -m -G adm,admin john
password john
```

---

### Post by yurtfg89327tfg0o on 2006-11-14
Yep gone completely. It was a fresh install so nothing valuable was lost.
Thanks for the advice, I'll jot it down in case I need it sometime.

---

