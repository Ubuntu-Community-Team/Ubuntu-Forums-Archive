---
title: "How do I combine multiple flags on the command line"
date: 2017-10-09
forum: General Help
---

### Post by gr8 on 2017-10-09
I understand I can combine multiple flags back to back simply putting them back to back. Take for example the copy command. I can combine the archive (a) flag and recursive (r) flags in series like this:
***cp -ar file1 file2***

If I use the long forms (archive) and (recursive) what do I then do? This?
***cp --archive --recursive file1 file2***

or this?
***cp --archiverecursive file1 file2 ***

---

### Post by ajgreeny on 2017-10-09
Not if you use the long (--archive) version of the option notations, but you can if you use the short option notation, ie, **cp -ar**

See ***man cp*** for all details

---

