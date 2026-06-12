---
title: "how-to monitoring a text file or log file in terminal"
date: 2013-02-13
forum: General Help
---

### Post by as004 on 2013-02-13
I once read in the "serverguide" about a command about monitoring but I don't remember it
  here is how it works, it could set the refresh rate, 1s, 2s I remember it is used to monitoring the log file

---

### Post by graysky on 2013-02-13
tail -f /path/to/file

---

### Post by Habitual on 2013-02-14
> **graysky said:**
> tail -f /path/to/file

```
watch -n x "tail -f /path/to/file"
```
Where x is the refresh interval.

I've been known to use -n 0 before. :)

---

### Post by btindie on 2013-02-14
> **Habitual said:**
> ```
watch -n x "tail -f /path/to/file"
```
Where x is the refresh interval.

I've been known to use -n 0 before. :)

You don't need to use *watch* when you use *tail* with the *-f* option, it's pointless.

---

### Post by Habitual on 2013-02-14
> **btindie said:**
> You don't need to use *watch* when you use *tail* with the *-f* option, it's pointless.It's the only command I remembered that had a "refresh rate, 1s, 2s" associated with it.

---

