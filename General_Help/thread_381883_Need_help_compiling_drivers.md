---
title: "Need help compiling drivers"
date: 2007-03-11
forum: General Help
---

### Post by Noxneo on 2007-03-11
Hello everyone,

I need to use a Mimio XI device on one of my Ubuntu systems. I managed to find the source code for the driver; however I have absolutely no idea of how I have to compile/install the driver.

Here is the link: [http://www.cs.nmsu.edu/~mwilder/dl/idx.html](http://www.cs.nmsu.edu/~mwilder/dl/idx.html)


Any help greatly appreciated.

---

### Post by Bachstelze on 2007-03-11
This driver seems outdated, I tried to compile it against a 2.6.18 and a 2.6.20 kernel with no success...

---

### Post by Noxneo on 2007-03-11
Is there anyway it could be adapted ?

---

### Post by Bachstelze on 2007-03-11
Not without changing the code... By the way, it compiled successfully in Dapper, with the default 2.6.15 kernel :

```

# apt-get install build-essential linux-headers-$(uname -r)
$ cd
$ wget http://www.cs.nmsu.edu/~mwilder/dl/mimio-xi_linux.tar.gz
$ tar xzvf mimio-xi_linux.tar.gz
$ cd 020
$ export KERNEL_SOURCE=/lib/modules/$(uname -r)/build
$ make
# insmod ./mimio.ko

```

(commands prefixed with # must be run as root with e.g. *sudo*, of course # and $ are not part of the commands ;))

---

### Post by Noxneo on 2007-03-11
OK, thanks a lot for that. I'll use a Dapper Laptop when I need this module.

---

