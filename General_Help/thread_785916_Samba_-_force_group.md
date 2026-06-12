---
title: "Samba - force group"
date: 2008-05-07
forum: General Help
---

### Post by Fynn on 2008-05-07
Hi all,

I would like to force all files created via my Samba share to be created with the group www-data.  To this end I've added the following line to my smb.conf:

force group = www-data

This is a valid local group in Ubuntu.

However, when trying to connect through windows I get the error "the specified group does not exist".  If I comment out this line I can connect fine, (although not create files as www-data).

Any help appreciated.

---

### Post by ttabbal on 2008-10-04
I am getting this behavior as well. Any ideas?

---

