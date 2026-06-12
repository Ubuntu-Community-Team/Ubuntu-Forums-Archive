---
title: "[SOLVED] open terminal here"
date: 2007-05-31
forum: General Help
---

### Post by nga911 on 2007-05-31
how can i make a "open terminal here" option on gnome , help appreciated

---

### Post by Suzan on 2007-05-31
There's a package called "nautilus-open-terminal" in the universe respositories.

Install that package and after a reboot* you have that option with a rightklick.

* maybe a restart of nautilus (killall nautilus) is enough, I am not sure

---

### Post by floke on 2007-05-31
You don't have to reboot. At most, restarting X (ctrl-alt-del) will kick it into action ;)

---

### Post by reclusivemonkey on 2007-06-03
```

killall -9 nautilus

```

does it without having to restart X.

---

