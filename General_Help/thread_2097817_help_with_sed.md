---
title: "help with sed"
date: 2012-12-24
forum: General Help
---

### Post by SlugSlug on 2012-12-24
I need to replace 

```
Music/
```

with

```
/Music/
```

Thanks & happy crimbo :popcorn:

---

### Post by Lars Noodén on 2012-12-24
Initially I would say this one:

```

sed -e 's:Music/:/Music/:' 

```

But that would also match /Music/ too.

---

### Post by SlugSlug on 2012-12-24
Perfect Thanks!!

---

### Post by markbl on 2012-12-24
Slightly better:
```

sed -e 's:Music/:/&:'

```

---

