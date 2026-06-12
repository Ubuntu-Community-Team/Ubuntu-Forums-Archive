---
title: "Installing gcc without apt-get"
date: 2005-06-30
forum: General Help
---

### Post by xfreeman86 on 2005-06-30
Hello,

I've searched the forums on why I can't use gcc (not installed by default), and then how to install it, but all of the solutions involve apt-get or some other method requiring a direct connection to the internet. Here's my problem:

For some reason, my laptop will not connect to our cable internet service even though other (Windows) computers can. Thus, I cannot use apt-get, but I can use the other Windows computers to transfer any necessary files manually. Can anyone enlighten me to a simple way of installing gcc in this situation?

Thank you
- John

---

### Post by SGC on 2005-06-30
I'm not sure if this is the best to way to do it , but you can download gcc and it's dependencies from here:

gcc: [http://packages.ubuntu.com/hoary/devel/gcc](http://packages.ubuntu.com/hoary/devel/gcc)
cpp: [http://packages.ubuntu.com/hoary/interpreters/cpp](http://packages.ubuntu.com/hoary/interpreters/cpp)
cpp-3.3: [http://packages.ubuntu.com/hoary/interpreters/cpp-3.3](http://packages.ubuntu.com/hoary/interpreters/cpp-3.3)
gcc-3.3: [http://packages.ubuntu.com/hoary/devel/gcc-3.3](http://packages.ubuntu.com/hoary/devel/gcc-3.3)
gcc-3.3-base: [http://packages.ubuntu.com/hoary/devel/gcc-3.3-base](http://packages.ubuntu.com/hoary/devel/gcc-3.3-base)
libc6: [http://packages.ubuntu.com/hoary/base/libc6](http://packages.ubuntu.com/hoary/base/libc6)
libgcc1: [http://packages.ubuntu.com/hoary/libs/libgcc1](http://packages.ubuntu.com/hoary/libs/libgcc1)
binutils: [http://packages.ubuntu.com/hoary/devel/binutils](http://packages.ubuntu.com/hoary/devel/binutils)
libdb1-compat: [http://packages.ubuntu.com/hoary/oldlibs/libdb1-compat](http://packages.ubuntu.com/hoary/oldlibs/libdb1-compat)


Then put the downloaded files in one folder, and use this command:
```

sudo dpkg -i gcc_3.3.5-1_i386.deb cpp_3.3.5-1_i386.deb cpp-3.3_3.3.5-8ubuntu2_i386.deb gcc-3.3_3.3.5-8ubuntu2_i386.deb gcc-3.3-base_3.3.5-8ubuntu2_i386.deb libc6_2.3.2.ds1-20ubuntu13_i386.deb libgcc1_4.0-0pre6ubuntu7_i386.deb binutils_2.15-5ubuntu2.2_i386.deb libdb1-compat_2.1.3-7_i386.deb 

```

Make sure to change the files names in the command If you are not using i386 architecture.

---

