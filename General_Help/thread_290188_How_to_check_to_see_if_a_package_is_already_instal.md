---
title: "How to check to see if a package is already installed? (command line)"
date: 2006-10-31
forum: General Help
---

### Post by Pri0n on 2006-10-31
Is there a command that you can use to check to see if a package is already installed?

For example, on a RPM based system (Fedora Core, Red Hat), you can simply type:

rpm -q <package name>

and it will immediately let you know if that package has already been installed on your computer.

Is there something similar in Ubuntu?

Thanks.

---

### Post by deepwave on 2006-10-31
Yes there is.

Run dpkg -l <package-name> to list similarly named packages and their status.
dpkg -s <package-name> gives a detailed info blurb about a package.

---

### Post by Pri0n on 2006-10-31
That works.  Thank you.

---

### Post by fragos on 2006-11-01
If you know the name of the executable try "which".  I believe it only serches directories in $PATH.

---

