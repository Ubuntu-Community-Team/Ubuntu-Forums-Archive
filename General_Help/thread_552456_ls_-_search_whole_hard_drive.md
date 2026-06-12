---
title: "ls - search whole hard drive?"
date: 2007-09-16
forum: General Help
---

### Post by Alhazred on 2007-09-16
Hi guys.

I have read the fine ls man, but being slow on the uptake, have not figured this out.

I am looking for the ls switch that will allow me to search the whole hard drive for a specific file. For example, in windows, I would use:
c:\dir /s *.doc to get all .doc files.

So is there an equivalent ls switch that I can use as sudo from the root?

Many thanks.
Mick

---

### Post by peabody on 2007-09-16
don't use ls for that, use find

find / -name '*.doc'

---

### Post by strabes on 2007-09-16
I guess you could do something like this:```
ls -R / | grep .doc
``` or ```
find / -name *.doc
```

---

### Post by peabody on 2007-09-16
> **strabes said:**
> or ```
find / -name *.doc
```

It's REALLY, REALLY important to have quotes around the search term:

find / -name '*.doc'

leaving the star bare like that will cause it to be expanded if there are any doc files in the current working directory, leading to mass confusion.

---

### Post by happy-and-lost on 2007-09-16
I use *locate filenameortypeorwhatever*. Does the trick.

---

