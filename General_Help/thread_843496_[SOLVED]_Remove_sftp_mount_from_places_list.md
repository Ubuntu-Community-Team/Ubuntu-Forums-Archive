---
title: "[SOLVED] Remove sftp mount from places list"
date: 2008-06-28
forum: General Help
---

### Post by kempy1000 on 2008-06-28
Hello

I have a a sftp mount in my places menu it was added automatically when i used the connect to sever tool.
It was all fine but now that server has been replaced and updated and i want to remove the dead link in my places menu but i cant figure how to do it??

Thanks 
Chris

---

### Post by notarzt-hd on 2008-06-29
Hi Chris,

I just had the same problem - but found the answer:

edit the file "~/.gtk-bookmarks" -> there you can find the sftp mount. Simply remove the line, save, and with the next "Places" click it will be gone :)

Cheers,
Michael

---

### Post by kempy1000 on 2008-06-29
Works Perfectly Thanks!

---

### Post by dmweyer on 2011-05-05
does this actually remove the mount or just delete the shortcut?

---

