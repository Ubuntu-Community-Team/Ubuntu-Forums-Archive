---
title: "bash question"
date: 2008-07-10
forum: General Help
---

### Post by boblemur on 2008-07-10
hey all,

im trying to redirect in bash, an echo to a log but i always want it to appear on screen... is this possible without writing the line out twice once with >> and once with out it...

thanks in advance

---

### Post by conscious on 2008-07-10
Use **tee**.
```
man tee
```
[http://en.wikipedia.org/wiki/Tee_(command](http://en.wikipedia.org/wiki/Tee_(command))

---

### Post by iaculallad on 2008-07-10
> **boblemur said:**
> hey all,

im trying to redirect in bash, an echo to a log but i always want it to appear on screen... is this possible without writing the line out twice once with >> and once with out it...

thanks in advance

That will be:

```
lspci | tee lspci.txt
```

To output on screen while saving it in a file.

---

