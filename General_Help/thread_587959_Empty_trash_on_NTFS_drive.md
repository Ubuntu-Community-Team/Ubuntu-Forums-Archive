---
title: "Empty trash on NTFS drive"
date: 2007-10-23
forum: General Help
---

### Post by eekfonky on 2007-10-23
I have noticed that when I delete files on the NTFS disk I have that they are gone but not deleted. The space they used is still allocated. Please tell how I get to the .trash file on my NTFS disk so I can delete these pesky files

---

### Post by orange2k on 2007-10-23
When you delete files on the NTFS partition, you can use SHIFT+delete to remove  them completely.

It is wise to remember, that the NTFS-3G driver that enables read/write access is still beta and may malfunction in some situations: I experienced total data loss when I kept writing to a NTFS disk that was almost full: now that disk is totally unusable. Be carefull...

edit: ok, its not beta anymore...

---

### Post by renzokuken on 2007-10-23
it should just be in the top directory of the drive.

open the ntfs drive in nautilus, press Ctrl+H to show hidden files and you should see a floder named .Trash_*username*

---

### Post by LaRoza on 2007-10-23
If you mean emptying the trash that Windows uses, delete $RECYCLE.BIN

---

### Post by eekfonky on 2007-10-23
Worked like a charm.

Thanks a lot

Chris

---

