---
title: "suspicious rkhunter results, anything to worry about?"
date: 2008-04-16
forum: General Help
---

### Post by ken300 on 2008-04-16
Hi,

I ran rkhuter this morning & got results that looked OK except for the following lines:

 Checking for hidden files and directories       [ Warning ]
Warning: Hidden directory found: /etc/.java
Warning: Hidden directory found: /dev/.static
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs
Warning: Hidden file found: /dev/.tmp-2-0: block special (2/0)

I've done some surfing & it looks like the following line are nothing to worry about :
Warning: Hidden directory found: /dev/.static
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs

That still leaves:
Warning: Hidden directory found: /etc/.java
Warning: Hidden file found: /dev/.tmp-2-0: block special (2/0)

Does anyone know if these are anything to worry about?

Thanks

---

