---
title: "Script empties trash except .deb files"
date: 2020-08-17
forum: General Help
---

### Post by raleigh3 on 2020-08-17
This script works with any file except .deb files?

Anyone know why?

```
#!/bin/bash
find /home/andy/.local/share/Trash/expunged/ -type f -exec rm {} \;
find /home/andy/.local/share/Trash/files/ -type f -exec rm {} \;
find /home/andy/.local/share/Trash/info/ -type f -exec rm {} \;
find /media/andy/MAXTOR_SDB2/.Trash-1000/files/ -type f -exec rm {} \;

```

---

### Post by The Cog on 2020-08-18
They're not symlinks (type l) are they? Or owned by root? 
Can you post the result of "ls -l <filepath> for one of the un-deleted .deb files?

---

### Post by &amp;KyT$0P# on 2020-08-18
Why are you doing this instead of using trash-cli package?

---

### Post by kneutron on 2020-08-19
This is a duplicate thread to
[https://ubuntuforums.org/showthread.php?t=2449042](https://ubuntuforums.org/showthread.php?t=2449042)

---

### Post by oldfred on 2020-08-19
Closed see duplicate above.

---

