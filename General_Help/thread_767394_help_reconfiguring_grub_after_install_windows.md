---
title: "help reconfiguring grub after install windows"
date: 2008-04-25
forum: General Help
---

### Post by scragar on 2008-04-25
ok, so I just installed windows(I want to play games that wine doesn't support :( ), and reinstalled grub, at the time everything looked fine, but grub wouldn't mount anything, after changing the root to **(hd0,1)** from **(hd0,2)** it booted, however quickly died.

How do I correct the mapping so I don't have this problem anymore?

EDIT: solved, I just use grub's map option to force them correct.

I've got a new problem now though(need to press ctrl+D since fsck complains about /dev/sda2 being mounted when it comes to check it, but that's my / so it has to mount...), but I'll post that in a new thread(unless someone has a complaint about that)

---

