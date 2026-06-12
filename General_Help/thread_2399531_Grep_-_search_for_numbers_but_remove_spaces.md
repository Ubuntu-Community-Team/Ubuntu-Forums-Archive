---
title: "Grep - search for numbers but remove spaces"
date: 2018-08-26
forum: General Help
---

### Post by Kevin McCready on 2018-08-26
Is there are grep command to find "1 2 345" in a file by searching for "12335". The reason is that the file contains numbers separated by spaces to make it human friendly and readable. I don't want to strip all spaces then search, but if there's a command for that ...
Thanks

---

### Post by The Cog on 2018-08-26
grep '1 *2 *345' filename
the " *" means any number of spaces

---

### Post by Kevin McCready on 2018-08-26
Thanks heaps.

---

