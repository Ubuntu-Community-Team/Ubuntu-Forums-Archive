---
title: "update-alternatives --install --&gt; howto"
date: 2005-10-21
forum: General Help
---

### Post by vedro on 2005-10-21
Hello

I`m using Debian - since are (K)Ubuntu similar i`m asking here

I have installed through apt-get install gcc-3.3 (because after system upgrade I have gcc-4.0.2 which does not compile some aplications correct - but I would like to have it anyway on my system). So now when I type the gcc --version command in the console I get this:

gcc --version
gcc (GCC) 4.0.2 (Debian 4.0.2-2)
Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions. There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

When I type gcc -V 4.0 -v command I get this:

Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.0 --enable-__cxa_atexit --enable-libstdcxx-allocator=mt --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-gc=boehm --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.2 (Debian 4.0.2-2)

When I type gcc -V 3.3 -v command I get this:

gcc -V 3.8 -v
gcc: couldn't run 'i486-linux-gnu-gcc-3.8': No such file or directory
roko:/usr/bin# gcc -V 3.3 -v
Reading specs from /usr/lib/gcc-lib/i486-linux-gnu/3.3.6/specs
Configured with: ../src/configure -v --enable-languages=c,c++,ada --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --with-gxx-include-dir=/usr/include/c++/3.3 --enable-shared --enable-__cxa_atexit --with-system-zlib --enable-nls --without-included-gettext --enable-clocale=gnu --enable-debug i486-linux-gnu
Thread model: posix
gcc version 3.3.6 (Debian 1:3.3.6-10)

So out of this infos I think that I have installed both gcc versions, or?
In the /usr/bin are :
gcc
gcc-4.0
gccbug-3.3
gccmakedep
gcov-3.3
gcc-3.3
gccbug
gccbug-4.0
gcov
gcov-4.0

So, do I have correctly installed both versions of gcc?

If I have how can I switch betwen them with update-alternatives command? I know that I have to use the update-alternatives --install command but the thing is that I do not know how to do that. So could somebody help me with update-alternatives --install command --> more precise is the explanation the better is for me to understand.

If I have to create symlink, I do not know how to do that to --> so could you please explain me how to do that to?

Tnx in advance!

have a nice day.
bug

---

### Post by vedro on 2005-10-24
Realy no idea?
anyone?:(

---

### Post by tonysathre on 2005-10-24
have u installed build-essentials, if not
type sudo apt-get install build-essentials with the install CD in the drive

---

### Post by indusnecro on 2006-02-08
I do not know the correct method to do this.
but after hacking for a while, I got it worked like this.

```
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-3.4 60 --slave /usr/bin/g++ g++ /usr/bin/g++-3.4
```

```
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.0 40 --slave /usr/bin/g++ g++ /usr/bin/g++-4.0
```

and 
```
sudo update-alternatives --config gcc
``` to change it. this updates gcc and g++ at the same time. if u want only gcc part, leave the --slave part.

---

### Post by apiper on 2008-06-24
Thanks for this, I'm using a mix of gcc-3.3 and gcc-4.2 and your howto really helped.

However, I have an addition that makes **gcov** work properly too!

Here's the commands I used. First of all, I erased the current update-alternatives setup for gcc:
```

sudo update-alternatives --remove-all gcc

```

Then I entered the following commands, which tie gcc, g++ and gcov together (note that the code in each box is a single command - I've split it into multiple lines using '\' to make it easy to read):
```

sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.2 42 \
--slave /usr/bin/g++ g++ /usr/bin/g++-4.2 \
--slave /usr/bin/gcov gcov /usr/bin/gcov-4.2

```
```

sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-3.3 33 \
--slave /usr/bin/g++ g++ /usr/bin/g++-3.3 \
--slave /usr/bin/gcov gcov /usr/bin/gcov-3.3

```

Choosing which version to use is achieved in the same way as before:
```

sudo update-alternatives --config gcc

```

I hope this helps others too :)

---

