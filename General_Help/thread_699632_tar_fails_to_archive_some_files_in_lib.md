---
title: "tar fails to archive some files in /lib"
date: 2008-02-17
forum: General Help
---

### Post by Red Shift on 2008-02-17
I'm running 64-bit Kubuntu 7.04 and I've used [this](http://ubuntuforums.org/showthread.php?t=81311) method to backup the entire system for at least eight months.

Since December, tar runs into problems in /lib and stops for at least three files:
/lib/libdl.so.2 (A link to /lib/libdl-2.5.so, a shared library)
/lib/libuuid.so.1.2 (A shared library)
/lib/libthread_db-1.0.so (A shared library)

All other directories (/, /usr, /home, etc) are successfully created when I exclude /lib.

Has anyone experienced or solved this problem?

Thank you in advance for your time.

---

