---
title: "Password protected archive (i.e zip) How To?"
date: 2007-10-18
forum: General Help
---

### Post by Sigurney on 2007-10-18
I'm looking for a way to password protect and encrypt an archive (.zip, .rar etc) so that when I proceed to open the archive (not in terminal) I am prompted for a password. Is there any graphical utilities that allow me to do this? I am using Ubuntu 7.10, Gnome 2.20.

---

### Post by p_quarles on 2007-10-18
This ought to do it:
```
zip -e *archivename*.zip *path/to/file*
```
The "-e" option will prompt you to enter a password, and then encrypt the file. 

Be advised, though, that this type of encryption isn't that hard to break. For anything really critical, you should use an encrypted filesystem.

---

