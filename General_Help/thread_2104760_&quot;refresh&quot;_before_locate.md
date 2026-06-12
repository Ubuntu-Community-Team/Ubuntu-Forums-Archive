---
title: "&quot;refresh&quot; before locate?"
date: 2013-01-14
forum: General Help
---

### Post by marchelloUA on 2013-01-14
Hi all, 

I've installed some package manually and can't find where it is installed. Tried 

*# locate foo*

but got no result. Should I use some "refresh" command before locate?

---

### Post by SlugSlug on 2013-01-14
```
sudo updatedb
```you can also use 

```
which foo
```

---

