---
title: "Problem with file-roller and samba"
date: 2016-02-03
forum: General Help
---

### Post by luca-vercelli-to on 2016-02-03
I have mounted on my laptop a remote shared folder smb://...
The mount works, and I have read and write permissions (tested using gedit)
However, file-roller cannot create new archives on that folder, it says "not enough permissions" (or somethig so, the error message is in Italian: "Permessi non sufficienti per creare un archivio in questa cartella").

With more precision. File-roller is started (by GUI) with the following command line:
file-roller --default-dir=smb://192.168.200.3/alkecondivisa/myfolder --add smb://192.168.200.3/alkecondivisa/myfolder/file1 smb://192.168.200.3/alkecondivisa/myfolder/file2

A dialog box opens, asking me if I want to compress such files. I choose the "zip" format, then press OK, and file-roller gives me the error I just wrote.

Can anyone help me?

Thank you.

---

