---
title: "set file permissions right for synchronizing network folders"
date: 2014-07-09
forum: General Help
---

### Post by DrScum on 2014-07-09
Problem: trying to synchronize network folders using grsync I continuously get error messages indicating "permission denied"

Here is how I do it: I mount the source folder on the target machine. User on source machine and target machine are the same, thus the file permissions should be set correctly. I have played around setting permissions using chmod -R (recoursively) but sometimes still get error messages.

Here are my questions: if I mount a network folder from machine A (source folder) to a folder on machine B (target folder) and run grsync on machine B how do I have to set the permissions in order to have a complete clone of the source folder in the target folder?

---

### Post by vanadium on 2014-07-09
You do not indicate how the network folder is mounted. This determines whether the mount supports linux permissions or not.

---

### Post by DrScum on 2014-07-09
sudo mount -t cifs //ip/<source-share> /<target-share>

---

### Post by cariboo on 2014-07-10
Thread closed by request.

---

