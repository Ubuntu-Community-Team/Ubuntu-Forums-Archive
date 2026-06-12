---
title: "Installer Troubles"
date: 2017-09-03
forum: General Help
---

### Post by Mazate on 2017-09-03
Howdy... I'm trying to install a .deb file to install my fluendo codec pack.  The installer keeps hanging up so I will need to do it in the terminal.  Unfortunately my knowledge of the linux command line is limited at best so I was wondering if anyone could give me the command do execute a .deb file.

Thanks!

---

### Post by westie457 on 2017-09-03
Hi, in the terminal cd to the directory holding the  deb file then sudo dpkg - i name_of_file.deb

---

### Post by ajgreeny on 2017-09-03
Or first install **gdebi** and open the .deb file with that. 

Whilst dpkg can install .deb packages it can not resolve any dependencies that are missing; gdebi deals with that just as apt or apt-get does when installing from the repos using the command line.

---

