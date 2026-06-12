---
title: "Pearpc, mac on linux"
date: 2008-04-14
forum: General Help
---

### Post by coninsan on 2008-04-14
Hi 

ive just gotten my copy of Mac OSX, and now the experiments start, i wish to run it on linux via an emulator, ive found PearPC.
But i cant install it, i am quite new to compiling so someone please help, it would be really nice :)

So the topick is, how to install Pearpc

---

### Post by joselin on 2008-04-14
What is the error you received?

The compiling process is really easy.
[http://pearpc.sourceforge.net/getstart.html#use_the_source_luke](http://pearpc.sourceforge.net/getstart.html#use_the_source_luke)

Regards

---

### Post by coninsan on 2008-04-14
when i try to use the first step of the guide i get this error:

```

checking for clock_settime in -lrt... yes
checking whether byte ordering is bigendian... no
checking for nasm... no
configure: error: *** 'nasm' missing, please install or fix your $PATH ***
```

---

### Post by ScorpKing on 2008-04-14
you need nasm. install it with sudo aptitude install nasm

---

### Post by joselin on 2008-04-14
Just do the following:
```
sudo apt-get install nasm
```

---

### Post by coninsan on 2008-04-14
now i get this error:

```
checking for nasm... /usr/bin/nasm
configure: error: Invalid parameter to --enable-ui: ''. Run './configure --help' for a list of valid parameters.

```

but it think it has something to do with that you have to edit something in this code:

```
./configure --enable-ui=$UI --enable-cpu=$CPU && make
```

---

### Post by coninsan on 2008-04-14
> Compilation from source

You will probably need to have GCC 3.x installed for the compilation to work. GCC 2.x should also work (if not write a patch). I don't recommend to use 3.0 <= GCC < 3.3 since they have severe bugs with -fomit-frame-pointer
Untar/gzip/bzip2 the downloaded file. Enter the created directory. Then compile by executing:

	$ ./configure --enable-ui=$UI --enable-cpu=$CPU && make
	

where $GUI is either x11, win32 or sdl and $CPU is either generic or jitc_x86. If you have an x86 processor you should use $CPU=jitc_x86. Everybody else uses $CPU=generic.

As of PearPC 0.3.0 the default configuration options are picked depending on your system, so a simple

	$ ./configure && make
	

should be enough in most cases. Continue with Configuration. 

i do not know how to edit the code to make it fit to my machine

---

