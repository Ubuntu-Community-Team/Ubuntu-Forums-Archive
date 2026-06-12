---
title: "deb package to replace config files at /etc"
date: 2007-06-11
forum: General Help
---

### Post by mlinsgomes on 2007-06-11
Hello everybody,

I have a machine that needs winbind, samba, pam and ldap packages to join in a domain and i tried to create a deb package that replace customized config files by the default files on that packages. But when i try to install, it doesn't work, the GDebi says that he couldn't replace files, and mark package as broken.
Anyone would please help me with this problem?

Thanks a lot,

---

### Post by smartboyathome on 2007-06-11
You cannot use .deb packages to do this, as it was a specification upon creating the package system. This is for security purposes.

---

### Post by mlinsgomes on 2007-06-11
then it's better to use a patch file? but if the patch don't match with the original file, don't they be replaced, right?

---

