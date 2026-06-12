---
title: "Uninstalling compiled software"
date: 2006-10-24
forum: General Help
---

### Post by allanlewis on 2006-10-24
Hi,

I recently compiled a few bits of software from source (e.g. the latest beta of gaim) and I was wondering how to uninstall software I installed in this way. Obviously I could delete /usr/bin/gaim (to use gaim as an example), but how about all the other stuff (e.g. the stuff in /usr/share)? How do I know where all that is? Is it just a matter of searching the whole file system for (continuing my example) "gaim" and deleting everything that I find? (Obviously, this would have to be done as root, or in Ubuntu terms, using sudo.)

Thanks in advance!

---

### Post by gborzi on 2006-10-24
You can try to use the uninstall target, if any in the makefile, i.e. > sudo make uninstall from the compiled source directory. As an alternative, you can use checkinstall. This program is used a follows: compile your source code, then make the installation with the command > sudo checkinstall make install It will ask a few questions, install the program and will make a .deb package with the installed files. Then use the package to uninstall (and eventually install). For further details look at the checkinstall manpage.

---

### Post by allanlewis on 2006-10-24
Thanks! :D

---

