---
title: "[SOLVED] Can you remotely log out a user?"
date: 2008-06-27
forum: General Help
---

### Post by TJP on 2008-06-27
If my kids or wife forget to logout can I log them out remotely, using ssh?

---

### Post by owlgorithm on 2008-06-27
```

sudo kill -9 $(ps -U KidOrWife -o "pid=")

```

---

### Post by owlgorithm on 2008-07-20
I know this thread is labeled "solved," but in case anyone is interested, this command is a bit easier to remember:
```

sudo killall -u KidOrWife

```

---

