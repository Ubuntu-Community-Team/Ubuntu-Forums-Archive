---
title: "Open file on SMB share with Openoffice"
date: 2007-09-04
forum: General Help
---

### Post by karl_kashofer on 2007-09-04
Hi !

I want to open a file located on an SMB share with openoffice. When I click on the file in konqueror i only see the openoffice splash screen, but oo never opens.
Any non-OO file type is properly opened on click in konqueror.

I seem to remember something about file locking, but setting SAL_ENABLE_FILE_LOCKING in the various soffice files does not help.
I do NOT want to mount the share every time I want to access a Openoffice file on it, besides, all the other apps can open files from the share.

I know i could do that from my previous feisty install which got hosed in a disk crash, just cant remember how i did it.

Any idea anyone ?

Thanks,
karl
Kubuntu Feisty on Macbook 13.3 2.16 Ghz

---

### Post by cwaldbieser on 2007-09-05
Since Oo is not part of KDE, it might not be able to use the smb:/ URL transparently like other KDE apps.  You might want to try mounting the share to a local folder with something like "smb4k" and try opening it that way.

---

### Post by karl_kashofer on 2007-09-05
Hi !

> **cwaldbieser said:**
> Since Oo is not part of KDE, it might not be able to use the smb:/ URL transparently like other KDE apps.  You might want to try mounting the share to a local folder with something like "smb4k" and try opening it that way.

Yes, I think you are right. Unfortunately mounting is not really an option for everyday use. I am quite surprised not more people are considering this a problem after all this works fine on the other OS.

Anyway, thanks for the suggestion, lets hope this is improved soon.

Cheers,
karl

---

