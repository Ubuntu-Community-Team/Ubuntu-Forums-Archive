---
title: "Formatting emails"
date: 2007-10-06
forum: General Help
---

### Post by linuxgeekery on 2007-10-06
I have a bit of a problem - 

I have a large list of emails formatted like this:
```
email1@something.com email2@something.com email3@something.com email4@something.com
```

and want to convert it into this format (newlines/returns after each email)
```
email1@something.com
email2@something.com
email3@something.com
``` 

I know I could do it manually, but it would take hours since there are over 2000.

I have a feeling that regular expressions could help here, but I don't know them other than "sed 's/a/b//" type thing.

Any help? :)

---

### Post by Jussi Kukkonen on 2007-10-06
```
perl -pi -e 's/ /\n/g' filename
```
should work if the file is well formed (no double spaces or anything). Note: it will modify the file, make a backup first if needed.

---

### Post by linuxgeekery on 2007-10-06
Thanks so much! It worked!

---

