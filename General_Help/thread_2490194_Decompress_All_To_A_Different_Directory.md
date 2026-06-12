---
title: "Decompress All To A Different Directory"
date: 2023-08-25
forum: General Help
---

### Post by wyattwhiteeagle on 2023-08-25
```
find /home/wyatt/Downloads/* -iname '*.zip' -execdir unzip {} \;
```
How do I decompress all zip files in one directory into another single directory?

The command above decompresses to the same directory.

---

### Post by ne29914 on 2023-08-25
-d option.
Check 'man unzip' in the terminal.

---

### Post by wyattwhiteeagle on 2023-08-25
> **wyattwhiteeagle said:**
> ```
find /home/wyatt/Downloads/* -iname '*.zip' -execdir unzip {} \;
```
How do I decompress all zip files in one directory into another single directory?


The command above decompresses to the same directory.
> **ne29914 said:**
> -d option.
Check 'man unzip' in the terminal.
According to the man page, it would change to...
I hope this is correct
```
find /home/wyatt/Downloads/* -iname '*.zip' -execdir unzip -d /home/wyatt/Desktop/Unzipped
```

---

