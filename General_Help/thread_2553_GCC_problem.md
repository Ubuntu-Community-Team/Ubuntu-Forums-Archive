---
title: "GCC problem"
date: 2004-10-29
forum: General Help
---

### Post by ToWAH on 2004-10-29
i tried to compile but :
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable cc found in $PATH
if i try to open synaptic packet manager ask for root passw, ?¿??¿  why i cant do a root account ? 
Well doing sudo /usr/sbin/synaptic works opened but gcc 3.3 & 3.4 base are installed ......
its a PATH problem ? how i must do to correct the PATH then?
thanks in advanced

---

### Post by diebels on 2004-10-29
Think you need to install the package named "gcc" which provides /usr/bin/gcc -> gcc-3.3. For synaptic, you enter your own password in the dialog box, not root password.

---

### Post by diebels on 2004-10-29
and install "autoconf" too

---

### Post by Dracontopes on 2004-10-29
Ubuntu has no root account, although not activated. For starting various applications like Synaptic just use your own password for your account. Search for gcc and install that package and you're done. :)

---

### Post by cacofonix on 2004-10-29
[QUOTE=ToWAH]i tried to compile but :
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable cc found in $PATH
if i try to open synaptic packet manager ask for root passw, ?¿??¿  why i cant do a root account ? 
Well doing sudo /usr/sbin/synaptic works opened but gcc 3.3 & 3.4 base are installed ......
its a PATH problem ? how i must do to correct the PATH then?
thanks in advanced[/QUOTE]


did you try sudo make? you might need to have root access to compile your program as it is being installed outside your home directory

---

### Post by WW on 2004-10-29
Did you first install the buld-essential package?
```
$ sudo apt-get install build-essential
```
This gets gcc, make, and other related packages that are needed for compiling programs.

---

### Post by ToWAH on 2004-10-30
[QUOTE=WW]Did you first install the buld-essential package?
```
$ sudo apt-get install build-essential
```
This gets gcc, make, and other related packages that are needed for compiling programs.[/QUOTE]
nope but all works perfectly , so installed gcc and the rest needed via sypnatic
thanks

---

