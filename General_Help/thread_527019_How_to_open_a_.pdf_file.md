---
title: "How to open a .pdf file"
date: 2007-08-16
forum: General Help
---

### Post by satimis on 2007-08-16
Hi folks,

Ubuntu 7.04 lamp server amd64
Fluxbox desktop
Rox-filer - File Manager
xpdf


How to make the .pdf files on the "File Manager" started with mouse pointer clicking on their icons?

$ ls -al /home/satimis/.config/rox.sourceforge.net/MIME-types/```

total 16
drwxr-xr-x 2 satimis satimis 4096 2007-08-16 18:23 .
drwxr-xr-x 4 satimis satimis 4096 2007-08-16 18:11 ..
-rwxr-xr-x 1 satimis satimis   22 2007-08-16 18:13 application_pdf

```

$ cat ~/application_pdf```

#! /bin/sh
exec  "$@"

```


Tried changing
exec "$@"
as
exec "xpdf"

or as
exec  xpdf

w/o result.  xpdf started w/o the file evoked/displayed.


Pls help.  TIA


B.R.
satimis

---

### Post by praet on 2007-08-16
Just a comment, the default ubuntu settings seem to use evince Document Viewer to view pdf files.
Right click a pdf file and select Open with Other Application.. select Document Viewer.

---

### Post by RedSquirrel on 2007-08-16
> **satimis said:**
> How to make the .pdf files on the "File Manager" started with mouse pointer clicking on their icons?

```
#! /bin/sh
exec xpdf "$@"

```

... but it's easier just to use the GUI. right-click on a file of type .pdf, and select "Set run action" and set it as:

```
xpdf "$@"
```

---

