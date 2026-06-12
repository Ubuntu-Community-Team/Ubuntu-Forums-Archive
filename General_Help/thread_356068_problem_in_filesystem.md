---
title: "problem in filesystem?"
date: 2007-02-08
forum: General Help
---

### Post by grado on 2007-02-08
I ran find command to search some files and I got this warning. Should I do something about it or just ignore? fsck gave me a clean chit though.

[FONT="Courier New"]
find: WARNING: Hard link count is wrong for /proc/5012: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.
[/FONT]

additional info:
[FONT="Courier New"]$ ps -eaf | grep 5012
www-data  5012  5010  0 00:11 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL

$ uname -a
Linux 2.6.17-10-386 #2 Tue Dec 5 22:26:18 UTC 2006 i686 GNU/Linux
[/FONT]

---

### Post by foo Utu on 2007-02-08
those /proc/<number> directories are automagically created by the /proc filesystem while a process is running. they provide diagnostic information.

often, a process may end while you are searching through /proc and so you can probably safely ignore this error.

---

### Post by grado on 2007-02-08
So I thought, but the warning message was spooky that I wanted to ask here.

Thank you.

---

