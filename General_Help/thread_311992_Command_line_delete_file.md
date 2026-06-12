---
title: "Command line delete file"
date: 2006-12-03
forum: General Help
---

### Post by georgecm3 on 2006-12-03
Hey everyone,

I unknowingly filled up my ubuntu partition ](*,)  and now I can not start x because there is no space to create the temporary files to start x.
Can anyone tell me how I can delete a program using the command line?
Thanks

---

### Post by kevinlyfellow on 2006-12-03
rm <filename>     to remove files
apt-get remove <package name>     to uninstall packages

---

### Post by soaring747 on 2006-12-03
to remove a directory along with all of its contents, type:

 rm -fr <directory>

use this with caution as there is no undelete.

I would suggest using gparted on the live CD to make more room though. Simply resize/shrink a parition adjacent to the one that Ubuntu's on, and resize/increase your Ubuntu partition.

---

### Post by georgecm3 on 2006-12-03
thank you. I will try that.

---

