---
title: "Countdown on shell scripts"
date: 2013-09-25
forum: General Help
---

### Post by vonvic on 2013-09-25
Is there a way to do account down without using echo sleep clear multiple times?

---

### Post by Habitual on 2013-09-25
> **vonvic said:**
> Is there a way to do account down without using echo sleep clear multiple times?
Define "multiple times"...There's a few ways... most involve loops using sleep; clear and echoes.

Are you trying to avoid repetition of these commands, or looking for alternatives to them?

---

### Post by Impavidus on 2013-09-26
```
for i in {10..1}; do echo -en "Launch in $i \r"; sleep 1; done; echo 'And we have liftoff!'
```
In echo, -n suppresses the newline and -e enables the interpretation of \r. \r causes the cursor to return to the beginning of the line, so that the next line overwrites the previous. The space after $i overwrites the 0 in 10 after the first iteration.

---

