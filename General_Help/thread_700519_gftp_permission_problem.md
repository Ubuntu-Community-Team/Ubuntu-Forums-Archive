---
title: "gftp permission problem"
date: 2008-02-18
forum: General Help
---

### Post by Dailydog on 2008-02-18
Hi

I use gftp to upload pfd files. My pupils should be able to download those from a site, but every file I've uploaded with gftp gives an error 403 message: permission denied.

How can I stop this?

---

### Post by matt91 on 2008-02-18
In gftp right click on the files > Chmod and make sure they are selected to read on User, Group and Other. That would be my first guess

---

### Post by Dailydog on 2008-02-18
That does work, but I'd like to find out why the permissions change once the files are uploaded. I used Filezilla before and never had that problem.

---

### Post by matt91 on 2008-02-18
Maybe becouse the FTP server sets the perms of all uploaded files to that. I'm not that sure but i think filezilla might set perms once uploaded but gFTP doesn't. My FTP server defaults to 755 on uploads anyway.

---

