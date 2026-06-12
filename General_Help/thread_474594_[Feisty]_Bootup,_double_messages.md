---
title: "[Feisty] Bootup, double messages"
date: 2007-06-15
forum: General Help
---

### Post by Snakiej on 2007-06-15
Hiya, 

I tweaked my Feisty a little, custom kernel and stuff, but now I'm seeing bootmessages double.

Like:
```
Reading Files to boot...
Reading files to boot... [ok]

Starting mysqld...
Starting mysqld...       [ok] 
```

Bit annoying. Anyway to fix this?

Has it anything to do with concurrency=shell maybe? :)

---

### Post by Snakiej on 2007-06-15
Well, I just checked, and it actually does cause the double boot messages.

And I didn't gain any speedups, so I leave it this off :)

---

