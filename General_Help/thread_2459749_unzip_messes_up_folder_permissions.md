---
title: "unzip messes up folder permissions"
date: 2021-03-25
forum: General Help
---

### Post by mcyber4 on 2021-03-25
Unzipped two ca. 500MB zip files. Permissions are fine in Windows and also correctly extracted on Mac. But on Ubuntu it sets on both unzips one folder to read only instead of read/write.
Where to report a bug?

---

### Post by ajgreeny on 2021-03-25
What exactly do you mean by **"Permissions are fine in Windows"**?

Windows does not see nor make any use of Linux permissions so I'm not sure about your problem; how are you unzipping the archive, using a GUI or command line?

---

### Post by TheFu on 2021-03-25
> **mcyber4 said:**
> Unzipped two ca. 500MB zip files. Permissions are fine in Windows and also correctly extracted on Mac. But on Ubuntu it sets on both unzips one folder to read only instead of read/write.
Where to report a bug?

The manpage for zip on my 20.04 system has *no mention at all* about permissions. This tells me that the umask will control how files and directories pulled from a ZIP are created.

The unzip manpage says this:
```
       Dates, times and permissions of stored directories are not restored except un&#8208;
       der Unix. (On Windows NT and successors, timestamps are now restored.)
```
So, if the zip was created on a Unix system, then unzip will try to recreate those permissions and timestamps.
If the zip was created on Windows, you get what you get.

There's a reason people use tar.gz files on Unix.

---

