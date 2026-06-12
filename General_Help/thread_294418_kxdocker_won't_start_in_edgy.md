---
title: "kxdocker won't start in edgy"
date: 2006-11-06
forum: General Help
---

### Post by darkenedday on 2006-11-06
I install kxdocker using synaptic in Kubuntu Edgy, when i run Kxdocker from the terminal i get this output

mike@Apollo:~$ kxdocker
KXDocker Will use Composite Extensions!
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kxdocker: WARNING: Cannot find updated resources: you may need to update or reinstall KXDocker resources, checkout [http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources](http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources)
kxdocker: WARNING: loading xml...
kxdocker: WARNING: Warning user kxdocker_conf.xml may be corrupt: loading last backup!
kxdocker: WARNING: Warning user, and backup configurations are corrupt! I'm going to load system kxdocker_conf.xml !!!
kxdocker: WARNING: Warning user, backup, system configurations are corrupt! please install right kxdocker_conf.xml
ERROR: Communication problem with kxdocker, it probably crashed.

any ideas?

thanks in advance!

---

### Post by vitorsouza on 2006-11-08
I think kxdocker is broken on Edgy...

What solved the problem for me was install the Debian testing package. Fortunately, I got no dependency conflict and it worked quite well.

These are the packages I downloaded and installed:
[http://packages.debian.org/testing/x11/kxdocker](http://packages.debian.org/testing/x11/kxdocker)
[http://packages.debian.org/testing/x11/kxdocker-data](http://packages.debian.org/testing/x11/kxdocker-data)

Hope it works for you,

Vitor Souza

---

### Post by vitorsouza on 2006-12-07
Just wanted to add: I reinstalled Kubuntu Edgy from scratch (the last time I had used apt-get dist-upgrade) and kxdocker still doesn't work. I changed it to kooldock and it has suited me well.

Vítor

---

