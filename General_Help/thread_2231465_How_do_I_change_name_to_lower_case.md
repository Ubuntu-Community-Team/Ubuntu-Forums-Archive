---
title: "How do I change name to lower case"
date: 2014-06-25
forum: General Help
---

### Post by Hewjr100 on 2014-06-25
This is what I have in terminal:

henry@Wyatt:~$

Can I change the W to lowercase or the h to uppercase? I would like both to be the same.

Henry

---

### Post by sandyd on 2014-06-25
Its easier to change the W to lowercase :D

do
```

sudo nano /etc/hosts

```
Change 'Wyatt' to 'wyatt' and press control+x to save

then
```

sudo nano /etc/hostname

```
Change it there too

Run
```

sudo hostname -F /etc/hostname
```

Open another terminal (or restart) and the hostname should be set.

---

### Post by Hewjr100 on 2014-06-25
Thanks for your assistance.

Henry

---

