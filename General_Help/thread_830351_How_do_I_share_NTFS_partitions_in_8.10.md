---
title: "How do I share NTFS partitions in 8.10?"
date: 2008-06-15
forum: General Help
---

### Post by rene mauricio on 2008-06-15
When I try to share /media/windows I get this error:

> 'net usershare' returned error 255: net usershare add: cannot share path /media/windows as we are restricted to only sharing directories we own.

	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.

Problem is I have no idea where to add it, because every place I have tried fails to allow me to share my Windows folder. Any help would be appreciated.

---

### Post by plucky on 2008-06-16
Did you try **/etc/samba/smb.conf**?

You have to logout and log back in to get it to work.


Good Luck

---

