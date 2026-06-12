---
title: "unable to open files list file..."
date: 2007-08-19
forum: General Help
---

### Post by baklava on 2007-08-19
Whenever I try to use apt to upgrade or install a package it gives me an "unable to open files list file for package `lftp': Permission denied" error. Looking over at this thread...
[http://ubuntuforums.org/showthread.php?t=249474](http://ubuntuforums.org/showthread.php?t=249474)

It advises removing the broken list file and reinstalling the package. However, I can't seem to be able to delete /var/lib/dpkg/info/lftp.list it gives me a permission error, even if I'm using nautilus in superuser mode, and it does the same with 'sudo rm'.
How can I fix this?

---

### Post by baklava on 2007-08-19
I've also tried editing the file with Gedit and nano, with still a permission error.

---

### Post by baklava on 2007-08-19
Anyone? Please? I really don't want to format again. :(

---

### Post by Samma3l on 2007-08-19
without wanting to sound condecending, have you tried sudo?

---

### Post by baklava on 2007-08-19
Yes, I have. Even in sudo, rm gives me
```
rm: cannot remove `/var/lib/dpkg/info/lftp.list': Permission denied
```

---

### Post by baklava on 2007-08-19
I tried booting into the LiveCD and using the 'sudo rm -f /var/lib/dpkg/info/lftp.list' command, but I rebooted into my hard drive and it's still there. I get the feeling I'm doing something stupid.

---

