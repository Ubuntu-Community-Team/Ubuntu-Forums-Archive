---
title: "NTFS USB HD shared with Samba + Nautilus error"
date: 2008-01-10
forum: General Help
---

### Post by pubo68 on 2008-01-10
Hi everybody,
I have Xubuntu as a samba server, sharing an External USB HD with NTFS. 

In the client (Feisty) I mount the share point with the command line (mount -t smbfs ....), and then I have full permissions (I can create files, directories, delete them, everything).

But if I try to do that (as the same user) with Nautilus, I can only create files, delete files, and delete directories, but I can't create new directories.

I have tested it with Thunar and Konqueror, and everything goes correctly, so...   could be this a Nautilus Bug?

¿How can I solve it? ¿Is there anybody with the same problem?

Thanks

---

### Post by pubo68 on 2008-01-10
Solved!
Finally it was a charset problem!! uhh!

client: mount -t cifs -o iocharset=utf8, .....
server (smb.conf): unix charset = UTF-8


Regards!

---

