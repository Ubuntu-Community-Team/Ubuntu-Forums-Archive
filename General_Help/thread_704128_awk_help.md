---
title: "awk help"
date: 2008-02-22
forum: General Help
---

### Post by I.You on 2008-02-22
Hi

I'd like to extract a field from a line in a file.
I was able to extract (e.g.) the 3rd field from all line:

> $ awk '{print $3}' test
(I.You)

DEV
dev8-0

tps
362.38

I want only the last line's (i.e. 362.38)
Any help?

Thanks in advance.

---

### Post by yabbadabbadont on 2008-02-22
Do you always just want the entire last line?  If so, the tail command can do that for you.  If not, you can use tail to grab the last line, and then pass it to awk to get the desired field from that line.

---

### Post by ghostdog74 on 2008-02-22
> **I.You said:**
> Hi

I'd like to extract a field from a line in a file.
I was able to extract (e.g.) the 3rd field from all line:



I want only the last line's (i.e. 362.38)
Any help?

Thanks in advance.

```

awk '{ last=$3}END{print last}' test

```

---

### Post by nick_h on 2008-02-22
or even just:
```
awk 'END {print $3}' test
```

---

### Post by yabbadabbadont on 2008-02-22
> **nick_h said:**
> or even just:
```
awk 'END {print $3}' test
```

Sweet.  You learn something new every day.  :D

---

### Post by ghostdog74 on 2008-02-26
> **yabbadabbadont said:**
> Sweet.  You learn something new every day.  :D
only if the last line is not a blank. just to take note.
```

awk 'NF{ last=$3}END{print last}' test

```

---

