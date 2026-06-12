---
title: "SWIG Code will Compile on One Computer, not on another"
date: 2016-07-16
forum: General Help
---

### Post by tim8 on 2016-07-16
What are the best things to check when code produces compiler errors on one computer, but not on another? The compile error looks like:

```

cparamlib_wrap.c: In function 'doubleArray___getitem__':
cparamlib_wrap.c:2720:5: error: invalid use of undefined type 'struct doubleArray'
     return self[index];
     ^
cparamlib_wrap.c:2720:16: error: dereferencing pointer to incomplete type
     return self[index];
                ^
cparamlib_wrap.c: In function 'doubleArray___setitem__':
cparamlib_wrap.c:2723:5: error: invalid use of undefined type 'struct doubleArray'
     self[index] = value;
     ^
cparamlib_wrap.c:2723:9: error: dereferencing pointer to incomplete type
     self[index] = value;

```

the lines of code it is referring to are:

```

SWIGINTERN double doubleArray___getitem__(struct doubleArray *self,size_t index){
    return self[index];
  }
SWIGINTERN void doubleArray___setitem__(struct doubleArray *self,size_t index,double value){
    self[index] = value;
  }

```

This is under gcc-4.8, but i've also tried under gcc-4.4.7. However, I've also run it on another linux computer (redhat in this case), and it compiles without any errors, using gcc-4.4.7. Unfortunately, I need to get the code working on the Ubuntu machine -- any suggestions on what to check? It looks to me like the compile environments are pretty similar except for the choice of gcc version, which I've tried to synchronize between both machines.

The gcc command it is failing on is:

```

gcc -DHAVE_CONFIG_H -I. -I..  -I/home/tim/Canopy/appdata/canopy-1.4.0.1938.rh5-x86_64/include/python2.7 -I../cparamlib   -g -O2 -MT _cparamlib_la-cparamlib_wrap.lo -MD -MP -MF .deps/_cparamlib_la-cparamlib_wrap.Tpo -c -o _cparamlib_la-cparamlib_wrap.lo `test -f 'cparamlib_wrap.c' || echo './'`cparamlib_wrap.c

```

---

### Post by steeldriver on 2016-07-16
Can you outline the exact steps that led to this failure? I just pulled the source from

[https://github.com/niklask/cparamlib.git](https://github.com/niklask/cparamlib.git)

and it seemed to build OK for me with

```

$ gcc --version
gcc (Ubuntu 4.8.5-2ubuntu1~14.04.1) 4.8.5

```

on Ubuntu 14.04

```

./autogen.sh
./configure --enable-python
make

```

---

### Post by tim8 on 2016-07-16
Thanks for the help! 

I believe I'm doing the same thing, just re-cloned to make sure we had the same version:

```

git clone [https://github.com/niklask/cparamlib.git](https://github.com/niklask/cparamlib.git)
cd cparamlib
./autogen.sh
./configure --enable-python
make

```

Which reproduces the error above. My gcc is one version behind:

```

gcc --version
gcc (Ubuntu 4.8.4-2ubuntu1~14.04.3) 4.8.4

```

my python version is:

```

python --version
Python 2.7.6 --  64-bit

```

which is part of Enthought's release:

```

which python
/home/tim/Enthought/Canopy_64bit/User/bin/python

```

My Swig version is newer than the computer I succesfully compiled on (which was 1.3.31), my computer has:

```

swig -version


SWIG Version 3.0.2


Compiled with /usr/bin/g++ [x86_64-unknown-linux-gnu]

```

---

### Post by steeldriver on 2016-07-16
Well I'm using the system versions of python and swig

```

Python 2.7.6

SWIG Version 2.0.11

```

My guess is that it is your SWIG version that is the issue

---

### Post by tim8 on 2016-07-16
Perfect! That seems to have done it, I had tried installing an older version of SWIG and linking to that -- without it working, but I now completely uninstalled the new version and now it seems to have worked.

Thanks!

---

