---
title: "Lost group membership for main user [Resolved]"
date: 2007-03-08
forum: General Help
---

### Post by akmet on 2007-03-08
Sorry to be a n00b, but in trying to be fancy, I've managed to remove the main (created during install) user from all of the security groups.  I have root access and have restored sudo access.  Looking for a list of group membership so I can re-add them all.  I'm sure there's a document out there somewhere, a point in the general direction would be fantastic.


Thanks

---

### Post by aysiu on 2007-03-08
You should belong to these groups: ```
adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
```

---

### Post by akmet on 2007-03-08
Thank you, that did the trick!

---

### Post by cdeel77 on 2007-03-27
YES, thank you!
Now I will always remember to type "usermod **-a** *groupname*"

---

