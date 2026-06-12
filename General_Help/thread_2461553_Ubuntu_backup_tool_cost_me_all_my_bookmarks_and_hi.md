---
title: "Ubuntu backup tool cost me all my bookmarks and history"
date: 2021-05-03
forum: General Help
---

### Post by sofasurfer on 2021-05-03
The Ubuntu backup tool (I think it is duplicity) won't let me get back my bookmarks and history. I backed up my home folder and then did a restore. Now when I open Firefox I get this message "The bookmarks and history system will not be functional because one of Firefox's files is in use by another application. Some security software can cause this problem." I managed to create a new profile and restore my bookmarks but I can not find how to restore my history.

---

### Post by HermanAB on 2021-05-03
The lsof command show which files are open by which processes, then you can kill the offending process.

---

### Post by rbmorse on 2021-05-03
After you did the restore from the backup, did you then reboot or at least log the user out and back in before running Firefox?

---

