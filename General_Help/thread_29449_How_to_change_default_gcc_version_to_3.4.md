---
title: "How to change default gcc version to 3.4?"
date: 2005-04-24
forum: General Help
---

### Post by lordmyth on 2005-04-24
If I install the C & C++ compilers version 3.4, 'gcc -v' still says 3.3.5... so how can I change that? I need it for running distcc server on this comp, because my other distro (gentoo) has 3.4.

---

### Post by lordmyth on 2005-04-24
There should be a more elegant solution, but for now I just changed all the symlinks in /usr/bin to the right version.

---

### Post by centered effect on 2005-04-24
How do you change the symlinks?

---

### Post by mendicant on 2005-04-24
Usually, this would be handled by update-alternatives, but the 3.3 to 3.4 change is not (necessarily) ABI compatible.  There are also distcc mechanisms for this--you would usually just call gcc-3.4 as the argument to distcc instead of just gcc.

---

### Post by sonni_kuba on 2005-09-02
This method works for x86_64 ubuntu, it should work too for the x86 version, albeit with some modifications.

Before we get started, install the following on your system through synaptics:

* cpp-3.4
* g++-3.4
* gcc-3.4
* gcc-3.4-base

First, let us go to the right directory

> cd /usr/bin

Let us check the default gcc version

> gcc --v

It should say 3.3.5

Now let us delete the old symbolic links

> sudo rm cpp gcc g++

Now let us change the symbolic links to 3.4

> sudo ln -s g++-3.4 g++ 
> sudo ln -s gcc-3.4 gcc
> sudo ln -s cpp-3.4 cpp 

Now we will delete the other symbolic links (THIS IS ONLY FOR x86_64 VERSION)

> sudo rm x86_64-linux-gcc x86_64-linux-g++ x86_64-linux-cpp

Again, let us change the symbolic links to 3.4

> sudo ln -s cpp-3.4 x86_64-linux-cpp
> sudo ln -s gcc-3.4 x86_64-linux-gcc
> sudo ln -s g++-3.4 x86_64-linux-g++

If you run to check the default gcc version

> gcc --v

It should now read 3.4.3

Hope this helps. If somebody could identify the x86 version of these symbolink links this would be great too.

x86_64-linux-gcc 
x86_64-linux-g++ 
x86_64-linux-cpp

---

