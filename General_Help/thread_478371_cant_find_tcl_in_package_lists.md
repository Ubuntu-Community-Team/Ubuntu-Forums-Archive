---
title: "cant find tcl in package lists?"
date: 2007-06-19
forum: General Help
---

### Post by Sir P on 2007-06-19
hi all,

trying to install tcl however says no release candidate when I try ... went to packages.ubunutu website and every single mirror says 404 file not found..

any ideas?

many thanks

> root@james-fiesty:/# apt-get install tcl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package tcl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package tcl has no installation candidate


Sir P :D

---

### Post by Sir P on 2007-06-19
ah have found the package im after now..here..

[http://mirrors.xmission.com/ubuntu/pool/universe/t/tcl8.0/tcl8.0_8.0.5-8.1_i386.deb](http://mirrors.xmission.com/ubuntu/pool/universe/t/tcl8.0/tcl8.0_8.0.5-8.1_i386.deb)

does anyone know how to install a remote .deb package?

i know on redhat you can use
#rpm -i [http://wwww.installpath/file.rpm](http://wwww.installpath/file.rpm)

is there similiar functionality on ubunutu ?

cheers all

---

### Post by YoG%*@ on 2007-06-19
hi

i believe it's ```
 sudo dpkg -i $debname 
```

hth
mux

---

