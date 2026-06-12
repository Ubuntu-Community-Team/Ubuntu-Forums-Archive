---
title: "root password"
date: 2008-01-08
forum: General Help
---

### Post by njb on 2008-01-08
++
Hello,
I tried to put my folders (bin,keys and script) in my var directory,
but I don't have permission to do it as far as i'm not the owner of the
var directory.
When I try to open a new session as root, don't have the password, could
you help ,

regards
:lolflag:
NjB
++

---

### Post by geirha on 2008-01-08
root has no password unless you have set one, and it doesn't need a password. To get a root-shell, type ```
sudo -i
``` in a terminal. If you want to run nautilus (the file browser) as root, run ```
gksudo nautilus
```

---

### Post by observ8 on 2008-01-08
[http://ubuntuforums.org/archive/index.php/t-514771.html](http://ubuntuforums.org/archive/index.php/t-514771.html)

---

### Post by njb on 2008-01-08
Thank you geirha and observ8, it's the first time I need help of the community, and I got it at the minute.
My problem is now solved with gksudo nautilus.
I could put my new folders in the var directory.
I hope next time I can chmod files and use my FTP client gFTP to edit files

:guitar:
NjB

---

