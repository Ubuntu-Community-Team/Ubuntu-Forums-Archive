---
title: "Can't Delete a database from MySQL"
date: 2008-05-25
forum: General Help
---

### Post by cward002 on 2008-05-25
I was finally able to get MySQL installed and working today.:) I was able to create a database from the commandline using the CREATE DATABASE command. I was also able to delete it using the DROP DATABASE command. However, The database still appears in the schema list in the graphical MYsql administrator. Is there a way to delete that entry?

Thank you

Colin

---

### Post by Monicker on 2008-05-25
It may just be cached in the gui.  Right click, Refresh, and it should be gone.

EDIT: I know the above works for the mysql query browser gui.  I can't recall offhand if the mysql administrator has the same  refresh option.

---

