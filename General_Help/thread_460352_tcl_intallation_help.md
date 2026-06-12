---
title: "tcl intallation help"
date: 2007-05-31
forum: General Help
---

### Post by uranous on 2007-05-31
Hi, here I am...again :)
I tried to install an eggdrop but I get an error about my tcl version is old or something like that, so I try to install a newer bersion of tcl following the instructions from [www.tcl.tk](www.tcl.tk) :

cd tcl8.4.14/unix
configure options (I type ''./configure'' coz ''configure options'' doesn't work)
make
make test
make install

But at the last step I get this:

```
make install
Installing libtcl8.4.so to /usr/local/lib/
cp: cannot create regular file `/usr/local/lib/#inst.24509#': Permission denied
mv: cannot stat `/usr/local/lib/#inst.24509#': No such file or directory
chmod: cannot access `/usr/local/lib/libtcl8.4.so': No such file or directory
make: *** [install-binaries] Error 1
```

Any suggestions on what I should do?

---

### Post by uranous on 2007-06-01
18 hours, any suggestion? :(

---

### Post by Wim Sturkenboom on 2007-06-01
You probably need root permissions. Try using sudo.

---

### Post by uranous on 2007-06-01
Thnx man i think it worked :D

---

