---
title: "How much space is _____"
date: 2012-12-20
forum: General Help
---

### Post by ceil210 on 2012-12-20
I know there is a command for this.  What is the command to check for files taking up "X" GB of space?  Thank you!

---

### Post by steeldriver on 2012-12-20
you mean something like this?

```
find /path/to/dir -size +*X*G
```

---

### Post by oldos2er on 2012-12-20
Something like ```
sudo du -h --max-depth=1 / | grep '[0-9]G\>'
``` ? See this thread: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by ceil210 on 2012-12-21
> **steeldriver said:**
> you mean something like this?

```
find /path/to/dir -size +*X*G
```


Just what I needed!  Thanks!

---

