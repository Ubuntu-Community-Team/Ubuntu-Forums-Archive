---
title: "Quick CLI ?"
date: 2014-06-14
forum: General Help
---

### Post by Kurt_Alan on 2014-06-14
[SIZE=5][COLOR="#000000"][/COLOR][/SIZE]

I have no problem unzipping single zipped files via cli but when I list a series of files separated only by a single space, I get a "no directory found."

What is proper syntax to indicate a series?

---

### Post by TheFu on 2014-06-14
Put the files with special characters in quotes.  Single or double quotes usually doesn't matter unless the filename has one of those. In that case, switch to the other quote types.

Post the exact command you are trying, for more specific help.

BTW, I don't think zip works on more than 1 file at a time. Check the manpage to be sure - **man zip**  ```

       zip  [-aABcdDeEfFghjklLmoqrRSTuvVwXyz!@$] [--longoption ...]  [-b path]
       [-n suffixes] [-t date] [-tt date] [zipfile [file ...]]  [-xi list]
```

Yep - only 1 zip file at a time.

---

### Post by Kurt_Alan on 2014-06-14
****

Thank you!

---

