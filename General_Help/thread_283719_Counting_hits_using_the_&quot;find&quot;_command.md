---
title: "Counting hits using the &quot;find&quot; command"
date: 2006-10-24
forum: General Help
---

### Post by DonQuixote on 2006-10-24
Hello all,

I'm wondering if there is a way of returning the number of "hits" for a search using "find".  ie: if I execute this command, "find . -name index.htm" and it returns 4 files, is there a way of returning jsut the number or the number of hits after the complete execution of the find command?

Thanks!

---

### Post by mssever on 2006-10-24
You could pipe it through wc -l. ```
find . -name index.htm | wc -l
```

---

### Post by DonQuixote on 2006-10-24
Awesome!  Thanks!

---

