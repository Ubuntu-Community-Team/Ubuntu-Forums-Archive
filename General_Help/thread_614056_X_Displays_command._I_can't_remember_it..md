---
title: "X Displays command. I can't remember it."
date: 2007-11-15
forum: General Help
---

### Post by oiper on 2007-11-15
I can't recall a command that lists the X displays being used/opened.
It would output all the displays ( :0 :1 :2 etc... ).

Anyone recall what this might be?

---

### Post by scorp123 on 2007-11-15
> **oiper said:**
> I can't recall a command that lists the X displays being used/opened. echo $DISPLAY  ... that would show on which display you're currently on. Was it that command you were looking for?

---

### Post by oiper on 2007-11-15
No. But good try. This command would spit out any and all X sessions that were opened. Listing them by their number.

I can't recall exactly what it spit out, but it was something like:

```

user1 :0
user2 :1
user5 :3

```

---

### Post by oiper on 2007-11-15
Well. I took to just reading an index of linux commands. I found it.... back in the w's.

The command is: **who**

---

### Post by scorp123 on 2007-11-15
Try these:
```
who
w
finger

```

---

