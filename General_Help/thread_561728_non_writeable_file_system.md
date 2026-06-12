---
title: "non writeable file system"
date: 2007-09-27
forum: General Help
---

### Post by bejamin1 on 2007-09-27
Some times when I use Adept my file system goes non writeable. It happens when Adept starts the install after it has downloaded the files. I have to back out do a restart that will fail because of a corrupt file system. I have to do fsck to fix the file system restart again then when I am back in KDE I have to go to terminal and do sudo dpkg --configure -a to finish the install.
  I am using 7.04 32 bit, fully updated.
  AMD dual 5600
  3 gigs of ram 
  Gigabite Mother board

 Thanks

 Ben

---

### Post by bejamin1 on 2007-09-29
In case anybody is interested. Adept did not completely load one program, It only loaded the package name and not the files, So it left a hole in the file system. Every time the hole was seen it created a file error and to protect it self the system when read only. I deleted the file and all is well. By the way it was a language pack for Open Office.

 Ben

---

