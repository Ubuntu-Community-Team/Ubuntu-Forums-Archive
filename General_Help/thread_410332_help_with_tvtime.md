---
title: "help with tvtime"
date: 2007-04-15
forum: General Help
---

### Post by wolfen69 on 2007-04-15
when i open tvtime, it says ivtv: invalid argument-cannot open capture device  /dev/video0
how do i fix this?

---

### Post by energiya on 2007-04-16
Well, do you have /dev/video0 ?
What is the output of
```

ls /dev/ | grep "video"

```
It might also be a permissions problem (if /dev/video0 is where is should), or a configuration problem for tvtime.

---

