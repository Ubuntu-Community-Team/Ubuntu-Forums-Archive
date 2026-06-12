---
title: "What is Ubuntus equivalence to this command &quot;chkconfig&quot;?"
date: 2008-04-25
forum: General Help
---

### Post by jingo811 on 2008-04-25
What is Ubuntus equivalence to this command "chkconfig"?
I've used it before on SuSE and I liked that command but it doesn't seem to exists on Debian and Ubuntu.  How does Ubuntu do these commands?

[http://linuxcommand.org/man_pages/chkconfig8.html](http://linuxcommand.org/man_pages/chkconfig8.html)
```
$ chkconfig --list
$ chkconfig telnet off
$ chkconfig telnet on
```

---

### Post by justleen on 2008-04-25
update-rc.d

though is not as "easy" as chkconfig.. if that doenst work for ya, try the package sysv-rc-conf

---

### Post by jingo811 on 2008-04-25
[http://wiki.kartbuilding.net/index.php/Sysv-rc-conf](http://wiki.kartbuilding.net/index.php/Sysv-rc-conf)
This one is even more intuitive than the "chkconfig" command on SuSE the only thing I miss now is green=On and red=Off and the ability to grep what I want to see.

---

