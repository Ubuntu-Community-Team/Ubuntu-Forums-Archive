---
title: "Is there any kind of &quot;recovery mode only&quot; blacklist?"
date: 2007-07-03
forum: General Help
---

### Post by Keyper7 on 2007-07-03
Hi all,

I recently found out that installing the nvidia binary drivers solved a problem
I had with the ehci_hcd module. Now I don't have to blacklist it anymore.

However, the solution doesn't seem to cover recovery mode (makes sense,
I think, since it is a text mode and the solution was video-related...).

So my question is... is there an easy way to blacklist a module only in recovery
mode? Or at least a way to add a sudo command to boot only in recovery
mode so I can do a modprobe -r ehci_hcd?

Thanks in advance,
-Keyper7

---

### Post by Keyper7 on 2007-07-03
* bump * no one?
I thought that there might be a simple solution...

---

### Post by Keyper7 on 2007-07-04
*bump* last try...

---

