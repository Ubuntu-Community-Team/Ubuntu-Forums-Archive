---
title: "multiple rar extraction?"
date: 2006-09-16
forum: General Help
---

### Post by nzk on 2006-09-16
I have 24 rar archives and its a pain to extract them one by one...

How do I extract them all to the same folder...at the same time?

---

### Post by ayoli on 2006-09-16
try this in a terminal:
```
cd /where/you/want/to/extract/
```
and then:
```
for i in `ls /path/where/are/*.rar`; do unrar e $i; done;
```

---

### Post by JMega on 2007-09-20
Thanks man. had the same problem. Love ;D

JMega

---

