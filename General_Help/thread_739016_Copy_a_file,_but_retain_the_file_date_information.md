---
title: "Copy a file, but retain the file date information?"
date: 2008-03-29
forum: General Help
---

### Post by marcadams on 2008-03-29
Hi All;

I've recently started using FlyBack up to protect my data.
Problem is when I restore the files, they loose their original date / time information ( the date is reset to to the date of the back up).

Looking at the backed up files, if I copy them manually via Nautilus, I get the same result.


**Question** - How can I copy a file from one location to another, where the target copy retains the date and time of the original??


Many thanks
Marc

---

### Post by insineratehymn on 2008-03-29
The copy command has a flag that says to preserve the originial attributes.

```
cp -p ORIGINAL_FILE BACKUP_FILE
```

The -p flag tells it to retain everything from permissions to timestamp.

---

