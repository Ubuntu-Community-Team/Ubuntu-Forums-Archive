---
title: "Setting file permissions"
date: 2008-05-08
forum: General Help
---

### Post by artti on 2008-05-08
I installed Command and Conquer 3 with Wine. I can't somehow set right permissions so that it can play with other computer account.

Can someone help me? I would appreciate it a lot.

---

### Post by TeoBigusGeekus on 2008-05-08
sudo chown username /path/to/exe/nameofexe.exe

---

### Post by chrisccoulson on 2008-05-08
The problem with Wine is that it doesn't support per-user registry entries at the moment (no multi-user support), so each user has their own wine 'C' drive (~/.wine/drive_c) and their own wine configuration. This means that installed applications are not shared between users.

The only way to share applications between users would be to move the 'C' drive to some area readable and writable to by all users, and modify each users wine configuration accordingly (I don't know how to do this though) to point to the new 'C' drive location.

Hope that helps

---

### Post by artti on 2008-05-08
Thanks. Now i know from wherei i should start.

---

