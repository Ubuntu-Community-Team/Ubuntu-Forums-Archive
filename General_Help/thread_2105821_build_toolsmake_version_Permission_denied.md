---
title: "build_tools/make_version: Permission denied"
date: 2013-01-17
forum: General Help
---

### Post by peacevisor on 2013-01-17
hello...
          i want to install asterisk from source file.
./configure is ok. But i typed ***sudo make*** the followint error occur.

/bin/bash: build_tools/make_version: Permission denied
/bin/bash: build_tools/make_version: Permission denied
make[1]: Entering directory `/home/peacevisor/Desktop/asterisk-11.0.1'
/bin/bash: main/version.c.tmp: Permission denied
make[1]: *** [main/version.c] Error 1
make[1]: Leaving directory `/home/peacevisor/Desktop/asterisk-11.0.1'
make: *** [_cleantest_all] Error 2


how can i solve this. Please help me.

---

### Post by ljmhk on 2013-01-17
Hi peacevisor,

Did you run the ./configure as root as well? If not try doing both the ./configure and then the make command as root

sudo su -
./configure
make && make install
exit

Alternatively could you use the apt sources or a deb file?

[https://wiki.asterisk.org/wiki/display/AST/Asterisk+Packages](https://wiki.asterisk.org/wiki/display/AST/Asterisk+Packages)

---

### Post by oldos2er on 2013-01-17
> **peacevisor said:**
> hello...
          i want to install asterisk from source file.
./configure is ok. But i typed ***sudo make*** the followint error occur.

/bin/bash: build_tools/make_version: Permission denied
/bin/bash: build_tools/make_version: Permission denied
make[1]: Entering directory `/home/peacevisor/Desktop/asterisk-11.0.1'
/bin/bash: main/version.c.tmp: Permission denied
make[1]: *** [main/version.c] Error 1
make[1]: Leaving directory `/home/peacevisor/Desktop/asterisk-11.0.1'
make: *** [_cleantest_all] Error 2


how can i solve this. Please help me.

Don't use 'sudo' except for the last step after 'make,' 'sudo make install'

```
sudo chown -R peacevisor:peacevisor /home/peacevisor/Desktop/

make
```

---

