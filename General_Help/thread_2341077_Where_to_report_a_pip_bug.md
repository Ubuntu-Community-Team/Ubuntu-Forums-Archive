---
title: "Where to report a pip bug"
date: 2016-10-24
forum: General Help
---

### Post by ineuw on 2016-10-24
I have a non-critical bug with pip 8.1.2 python 2.7 when installing through the terminal any software that uses it, and no clue where to report it. Spent a lot time searching for info but found nothing and information would much appreciated. 

> The directory '/home/ineuw/.cache/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.


Installation of the same software using 'Gnome Software Installer (Xubuntu 16.04) was problem free when the folders' and files' permissions were default. Now, I am the owner of all folders, subfolders and files in the Home directory and permissions are read, write, and execute for the same.  using the -H flag of sudo doesn't help, and it's annoying because the installation is successful.

---

### Post by cariboo on 2016-10-24
You can report the bug here:

[https://github.com/pypa/pip/issues](https://github.com/pypa/pip/issues)

---

### Post by monkeybrain20122 on 2016-10-24
I have been seeing this since Ubuntu 15.10, not sure what to make of it but it is harmless, I have no problem installing/uninstalling /updating with pip. I think if you use the flag -H as it says then the warning goes away.

---

### Post by ineuw on 2016-10-24
cariboo and monkeybrain20122: Thanks to you both for the info, and I already posted the bug report. I did try the -H switch but it didn't help.

---

