---
title: "TMP File Question"
date: 2013-01-25
forum: General Help
---

### Post by Longtrain on 2013-01-25
I noticed that in my File System there is a folder under TMP called "tmpjrZ4D0", that is locked and cannot be deleted even if I log in as root.  Can anyone tell me what this is, thanks...

Tony
Longtrain

---

### Post by mcduck on 2013-01-25
/tmp is used by the system and programs to store temporary files while they are working. You shouldn't have to worry about them at all (and actually deleting anything manually would most likely cause the service or program using the file to crash).

Anyway, everything in /tmp is automatically deleted when you reboot the system, so no need to worry about them eating your disk space... :)

---

### Post by elliotn on 2013-01-25
> **Longtrain said:**
> I noticed that in my File System there is a folder under TMP called "tmpjrZ4D0", that is locked and cannot be deleted even if I log in as root.  Can anyone tell me what this is, thanks...

Tony
Longtrain

TMP is a temporary folder it should be cleared when u log off...  I could be wrong

---

