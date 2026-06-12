---
title: "After 1h my folders appear with locks on them !!"
date: 2017-08-03
forum: General Help
---

### Post by sebastien-vautelin on 2017-08-03
Hello !

 I start to use my computer with Ubuntu Studio 16.04, and  after a while (maybe 1h) I can't delete any files, for they appear with  locks on them. I may have changed something in previous operations but I  have no idea what.
I tried to update but didn't change anything.

No idea of how to solve that issue.

Anyone can help me ?

Thank you !

---

### Post by ajgreeny on 2017-08-03
Show us the output in of command ```
ls -la
``` in terminal.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by Impavidus on 2017-08-03
My first guess (but only a guess) is that the files are read-only because the entire file system was remounted read-only. This can happen after an error during read or write to disk. In addition to ajgreeny's command, run```
findmnt
```and show us the output.

If this was indeed the problem and you have rebooted since it happened, the problem may be gone now – for a while. Still worth to investigate, because it could indicate failing hardware.

---

