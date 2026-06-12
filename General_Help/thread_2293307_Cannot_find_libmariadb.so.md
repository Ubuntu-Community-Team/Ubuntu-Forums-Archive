---
title: "Cannot find libmariadb.so"
date: 2015-09-04
forum: General Help
---

### Post by hugo29 on 2015-09-04
Hello!

I am attempting to run a 32bit program on a 64bit version of Ubuntu.

I succeeded in this by installing the i386 libraries, however this 32bit program also uses MySQL.

While attempting to connect to the MySQL server it produces the error:
"libmariadb.so: cannot open shared object file: No such file or directory"

I'm assuming that because I have a 64bit version of MySQL that the libmariadb.so is simply in a different place.

I know vaguely about symbolic links between files and I was wondering if anyone knows where libmariadb.so is in 64bit MySQL and where I need to link it to?


It may be however that i'm completely wrong and there's a completely different solution for this, either way I hope you can help.

Thanks!

(It may be worth noting that i'm SSH'ing onto an external server and I don't have access to a gui, only the terminal)

(I'm also using Ubuntu 14.04 i386)

---

### Post by patlkli on 2015-09-04
If your system is running a 64-bit Ubuntu (even though your last sentence said i386, not amd64 ;)) and you want to run a 32-bit program using MySQL, you'd also have to use a 32-bit MySQL library.

This shouldn't be a problem, since libmariadb provides libmysqlclient, however in 14.04, the MariaDB library was named libmariadbclient.so, and in 15.04 it was renamed to libmariadb.so.

Could it be, that the program you are trying to run, was compiled on a younger version of Ubuntu than 14.04?

---

