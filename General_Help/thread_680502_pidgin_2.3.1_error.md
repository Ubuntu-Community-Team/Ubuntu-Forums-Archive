---
title: "pidgin 2.3.1 error"
date: 2008-01-28
forum: General Help
---

### Post by nkobel003 on 2008-01-28
whenever i try to start pidgin, i get this error in the terminal:
```
pidgin: symbol lookup error: pidgin: undefined symbol: purple_account_get_current_error

```

anyone know what's going on?

---

### Post by nkobel003 on 2008-01-28
sorry for the re-post:
```

sudo apt-get remove pidgin
sudo apt-get purge libpurple0

```

bump

---

### Post by Castaa on 2008-02-11
I had the same issue and those two commands fixed the problem.  Thanks.

---

### Post by Paul_K on 2008-03-19
This fixed it for me for 2.4.0 as well running on Gutsy.

Thanks

-PaulK

---

