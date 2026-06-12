---
title: "Unable to authenticate installations"
date: 2013-10-27
forum: General Help
---

### Post by robertk1995 on 2013-10-27
I am currently running Lubuntu on a Windows laptop and am attempting to install various different packages. However when I am asked for my password, I get this error after entering it: 

Failed to run gdebi-gtk '--non-interactive' '/home/rob/Downloads/steam_latest (1).deb' as user root.


The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

I have removed the previous user from the system, making my user the admin, yet it still will not accept my password. Any ideas?

Thanks

---

### Post by Jeremy Reid on 2013-10-27
I'd try a clean install.

---

### Post by ajgreeny on 2013-10-27
I do not really know anything about installing steam, but assuming rob is your current username can you show the output from the command **groups** in terminal.

This is just to check that having removed the other users that you mentioned, one of whom may have been admin, you really are an admin user now as the one user remaining on the machine.

By default the first user you make during installation is the one with sudo/admin rights; any others added afterwards do not have the same admin rights unless you as first admin user give them those rights, and if you as admin user were to be removed later, none of the remaining users become admin automatically

---

