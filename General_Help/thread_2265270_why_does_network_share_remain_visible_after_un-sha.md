---
title: "why does network share remain visible after un-sharing"
date: 2015-02-13
forum: General Help
---

### Post by stupidquestion on 2015-02-13
On my Ubuntu machine I had a shared folder which could be accessed by Windows computers on the network. When I un-share the folder, it's supposed to disappear among the shared folders, but this shared name remains there, visible on the network. How do I remove this share permanently?

---

### Post by stupidquestion on 2015-02-13
It was because the folder was shared as an entry under /etc/samba/smb.conf which had to be removed manually.

---

