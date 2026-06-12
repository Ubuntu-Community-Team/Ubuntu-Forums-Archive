---
title: "dselect question"
date: 2006-07-08
forum: General Help
---

### Post by paulhide on 2006-07-08
I am running dapper-drake. I followed a recipe in [http://www.ubuntuforums.org/showthread.php?t=195093&highlight=webmin](http://www.ubuntuforums.org/showthread.php?t=195093&highlight=webmin)
to install webmin (does not use dselect). Now when I use dselect to look at installed packages there is no mention of it. Is this normal? I always imagined dselect reflected the packages that were actually installed.

---

### Post by Rui Pais on 2006-07-08
Hi, 
no because, following the instructions on the thread you point, you not installed through a deb package. So dselect knows nothing about. dselect, dpkg, apt and so on can only manage deb files.


*Edit:* there is an app, checkinstall, that allow to install non-deb apps  in a way that they can be managed by the standard package management utilities. But i think it's only efective when the installed app is a source code to be compilled with the usual .configure && make && make install. I never tried...

---

### Post by paulhide on 2006-07-09
Many thanks for the reply.

---

