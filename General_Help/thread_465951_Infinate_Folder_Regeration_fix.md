---
title: "Infinate Folder Regeration fix?"
date: 2007-06-06
forum: General Help
---

### Post by jpennin5 on 2007-06-06
When I backed my system up, I chose to save the backup to a folder that was inside the folder I was backing up.  This has resulted in the folder I saved the backup to, to infinately regenerate itself inside of itself.  I have tried to send the entire folder to the trash, but it didn't work (or it was so slow it would take a day or two to delete) does anybody know how I can fix this problem?

---

### Post by gerscht on 2007-06-06
instead of moving it into the trash folder, deleting the files on the command line would be the better solution.
Open terminal
```

rm  /the/folder/* -r

```
NOTE: this will delete ALL files within the folder, so use with care!

---

### Post by jpennin5 on 2007-06-06
Thanks!

---

