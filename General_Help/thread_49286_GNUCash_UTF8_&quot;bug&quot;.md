---
title: "GNUCash UTF8 &quot;bug&quot;"
date: 2005-07-15
forum: General Help
---

### Post by Omarkj on 2005-07-15
I've been trying to use GNUCash for my small business, but I have a big problem I need to figure out somehow. GNUCash uses Guppi, a old Gnome tool, that doesn't seem to handle UTF8 well.

When I run gnucash from shell without a "LANG" argument I am able to type in Icelandic letters but I'm unable to view record, invoices and so on with the Icelandic letters, they just look like UTF8 garbage.
```
$ gnucash
``` 

When I run gnucash in shell with a "LANG" argument Icelandic letters don't show up in the "type-in" window, but I am able to print out records, invoices and so on with the Icelandic letters.
```
$ LANG="is_IS" gnucash
``` 

Any ideas?

---

