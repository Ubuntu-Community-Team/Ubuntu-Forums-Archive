---
title: "How can I dump the content of a directory to a file?"
date: 2007-05-28
forum: General Help
---

### Post by yinglcs2 on 2007-05-28
Hi,

How can I walk thru a directory tree (include sub-directories), dump the name and the file size of each file to a file?

Thank you for any help.

---

### Post by energiya on 2007-05-28
```

ls -lRh DIRECTORY > file_name

```
and if you want to dump **only** name and size use:
```

ls -Rlh DIRECTORY | gawk  '{if ($8 == "") print $1"   "$2; else print $8"     "$5}' > file_name

```

---

