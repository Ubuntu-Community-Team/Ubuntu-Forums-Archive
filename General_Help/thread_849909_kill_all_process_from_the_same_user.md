---
title: "kill all process from the same user"
date: 2008-07-05
forum: General Help
---

### Post by dapim on 2008-07-05
this comand isn't working, i pretend kill all process for the user james

killall james
not even this
killall -9 james

---

### Post by sdennie on 2008-07-05
Try:

```

sudo pkill -u james

```

Or

```

sudo pkill -9 -u james

```

---

