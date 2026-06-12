---
title: "NTFS .Trash-username not working"
date: 2008-05-05
forum: General Help
---

### Post by drubix on 2008-05-05
Hi,
Previously (i.e. when using gutsy) if I deleted a file from an ntfs partition it ended up going to the root of that partition in .Trash-*username*.  I upgraded to hardy today and when I try to delete files nautilus warns me that they can't be moved to the trash and they never end up in the trash folder.  Is there some setup I need to do in order to get it working or are things done differently in hardy?
Thanks

---

### Post by Rocket2DMn on 2008-05-05
.Trash-username seems to be deprecated, now it uses .Trash-useridnumber, which for most people is .Trash-1000

---

### Post by neymac on 2008-05-05
> **Rocket2DMn said:**
> .Trash-username seems to be deprecated, now it uses .Trash-useridnumber, which for most people is .Trash-1000

When I delete the files from .Trash-1000 they appear again at the very same place (.Trash-1000). To delete permanently the files I need to delete .Trash-1000 directory .
Is there a fix for this issue?

---

### Post by drubix on 2008-05-05
I didn't even notice that new folder.  Thanks for that!

---

