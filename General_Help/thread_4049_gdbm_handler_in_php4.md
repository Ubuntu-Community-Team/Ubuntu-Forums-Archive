---
title: "gdbm handler in php4?"
date: 2004-11-11
forum: General Help
---

### Post by jalrnc on 2004-11-11
I'm trying to access an old php wiki (after replacing mandrake with warty, which rules by the way...) but I'm having trouble accessing the database. It looks like the gdbm handler was not enabled in the php configuration? Is there an easy way to enable it? Some other package I need to install? Do I have to get the source deb and enable gdbm in the php config?

```
lib/DbaDatabase.php:38: Fatal[256]: dba_open(pages/wiki_pagedb.gdbm,c): No such handler: gdbm
``` 

Any ideas? Thanks a lot.

João

---

### Post by jalrnc on 2004-11-13
Replying to my own post... I fetched the source deb for libapache2-mod-php4, added gdbm to the configuration, and built the package. Works like a charm, now I can use the gdbm handler for dba with php.

João

---

