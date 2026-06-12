---
title: "non empty folder in a NAS or other computer not deleted"
date: 2018-08-02
forum: General Help
---

### Post by herp-derp on 2018-08-02
good morning,
new installation of 18.04 standard ubuntu, if I try to delete a non empty folder in an NAS or in a shared folder in another computer (with lubuntu) all seems correct, but if I do a refresh of the folder, all the files remain intacts.
for remove all the items I have to delete all files before to delete the folder...
wtf??

thankyou

---

### Post by HermanAB on 2018-08-02
$ rm -rf directoryname

Don't ever use wild cards with that command.

---

### Post by westie457 on 2018-08-02
> [COLOR=#000000]$ rm -rf directoryname[/COLOR]

[COLOR=#000000]Don't ever use wild cards with that command.[/COLOR]

Also **do not**&#8203; have any spaces in path of that command.

---

### Post by herp-derp on 2018-08-03
ok,

but if I have a lot of folders and only some are to be deleted? is an issue of Nautilus or is a normal thing?


thank you

---

### Post by HermanAB on 2018-08-03
The command to delete a directory is completely different from the command to delete a directory full of files.  Nautilus only implemented the one.

---

