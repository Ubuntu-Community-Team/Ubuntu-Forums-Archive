---
title: "How can I correct these errors when I try to launch kxdocker?"
date: 2007-02-04
forum: General Help
---

### Post by maddbaron on 2007-02-04
> maddbaron@baronworks:~$ kxdocker
KXDocker Will use Composite Extensions!
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kxdocker: WARNING: Cannot find updated resources: you may need to update or reinstall KXDocker resources, checkout [http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources](http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources)
kxdocker: WARNING: loading xml...
kxdocker: WARNING: Warning user kxdocker_conf.xml may be corrupt: loading last backup!
kxdocker: WARNING: Warning user, and backup configurations are corrupt! I'm going to load system kxdocker_conf.xml !!!
kxdocker: WARNING: Warning user, backup, system configurations are corrupt! please install right kxdocker_conf.xml
ERROR: Communication problem with kxdocker, it probably crashed.


any help please?

---

### Post by wconstantine on 2007-05-01
Got the same problem.

---

### Post by jiminycricket on 2007-05-03
This bug: [https://bugs.launchpad.net/bugs/105423](https://bugs.launchpad.net/bugs/105423) (still unconfirmed :()

It seems like it was also a problem in Edgy,  they fixed it, but then it happened in Feisty.

I hope if it's fixed in Feisty, that they don't have to fix it again in Gutsy...

---

### Post by rebegin on 2007-05-03
installing debian packages worked for me:
[http://packages.debian.org/testing/x11/kxdocker](http://packages.debian.org/testing/x11/kxdocker)
[http://packages.debian.org/testing/x11/kxdocker-data](http://packages.debian.org/testing/x11/kxdocker-data)

---

