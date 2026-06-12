---
title: "Symbolic link to file not apparent?"
date: 2007-10-26
forum: General Help
---

### Post by acambre on 2007-10-26
I just made a symbolic link to /etc/phpmyadmin/apache.conf in /etc/apache2/conf.d per [http://ubuntuforums.org/showthread.php?p=3639434#post3639434](http://ubuntuforums.org/showthread.php?p=3639434#post3639434) using this command: **sudo ln /etc/phpmyadmin/apache.conf phpmyadmin.conf**

Doing an ls -l inside /etc/apache2/conf gives me this:
[B][username]@ubuntu:/etc/apache2/conf.d$ ls -l
total 8
-rw-r--r-- 1 root root 269 2007-10-04 17:42 charset
-rw-r--r-- 2 root root 983 2007-07-24 06:26 phpmyadmin.conf[/B]

Symbolic link directories show up differently on an ls. E.g.:
[B]
lrwxrwxrwx 1 root root       13 2007-10-25 16:27 motd -> /var/run/motd
[/B]

Why not files? How am I supposed to know that phpmyadmin.conf is a symbolic link?

---

### Post by nick_h on 2007-10-26
You have made a hard link rather than a symbolic link.  You need to use the -s option in the ln command.

---

### Post by acambre on 2007-10-26
> **nick_h said:**
> You have made a hard link rather than a symbolic link.  You need to use the -s option in the ln command.
That did it. Thank you!

---

