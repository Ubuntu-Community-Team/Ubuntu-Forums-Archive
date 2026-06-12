---
title: "ubuntu instalation isues"
date: 2007-06-09
forum: General Help
---

### Post by sinfin on 2007-06-09
after ubuntu instalation by Wubi , ubunto do not boot up properly....
....."" the program apt-get is correctly not installed.""...
then stop.

after hit " exit"... it continues on ubuntu windows.....  looks to me that there are isues with maintenance ???

any sugestions...:(

---

### Post by ago on 2007-06-09
It might be that ntfs is marked as dirty and it is mounted read only. Run chkdisk and try again, in case try to reinstall.

---

