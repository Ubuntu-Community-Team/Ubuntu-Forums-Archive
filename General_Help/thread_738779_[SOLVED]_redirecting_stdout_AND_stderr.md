---
title: "[SOLVED] redirecting stdout AND stderr"
date: 2008-03-29
forum: General Help
---

### Post by bilijoe on 2008-03-29
Is there a way to rediredc both sdtout and stderr to the same file, so you can capture the entire output of something like 'configure' in sequential order?

---

### Post by monraaf on 2008-03-29
This:
```

foo > bar 2>&1

```

will send **stdout** and **stderr** of *foo* to *bar*. But I wouldn't count on it to be in sequential order, because **stdout**  is normally buffered.

---

### Post by pointone on 2008-03-29
```
foo >& bar
```

... should be equivalent.

---

