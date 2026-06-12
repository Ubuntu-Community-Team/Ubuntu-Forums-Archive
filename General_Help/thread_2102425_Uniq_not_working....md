---
title: "Uniq not working..."
date: 2013-01-07
forum: General Help
---

### Post by sydalackk on 2013-01-07
running a uniq on a file and its not removing duplicates. Ran the same Uniq command last semester same way and it worked.

uniq file.csv > file2.csv

its still the same size and all.

---

### Post by SeijiSensei on 2013-01-07
Use sort first:

```
sort < file1 | uniq > file2
```

---

### Post by The Cog on 2013-01-07
uniq only compares adjacent lines. You may need to sort the file first, to get all the matching lines grouped together.
sort file.csv | uniq > file2.csv

---

### Post by sydalackk on 2013-01-07
still didn't work after using that command.

---

### Post by ivotkl on 2013-01-07
I do not know about uniq command, **but** I'm thinking that maybe something was changed on one file (don't know). Have you tried doing md5sum on both files to make sure they are **exactly** the same?

---

### Post by The Cog on 2013-01-07
And are you sure there are exact duplicate lines?
Are the files small enough to post?

---

