---
title: "Installing program from CERN, libgfortran.so.1 dependency for running a binary"
date: 2013-05-08
forum: General Help
---

### Post by mertinism on 2013-05-08
I'm currently trying to install/run a program called Garfield ([http://garfield.web.cern.ch/garfield/](http://garfield.web.cern.ch/garfield/)) for some simulations that I have to run - instructions here ([http://garfield.web.cern.ch/garfield/files/](http://garfield.web.cern.ch/garfield/files/)). The program is a 64-bit binary, so it's no problem that I'm running a 64-bit machine. I uudecoded and gunziped it. When trying to get it to run however, I received the following error.

```
./garfield-9: error while loading shared libraries: libgfortran.so.1: cannot open shared object file: No such file or directory

```

So, this program is dependent upon libgfortran1, a simple install of it should work. Except libgfortran1 is no longer in the repositories. Ok, fine. I have build-essential and libgfortran3 installed, so I'll make a symbolic link of libgfortran.so.3 and name the link as libgfortran.so.1

```
$ locate libgfortran.so.3
```

```
/usr/lib/x86_64-linux-gnu/libgfortran.so.3
/usr/lib/x86_64-linux-gnu/libgfortran.so.3.0.0
/usr/local/MATLAB/R2013a/sys/os/glnxa64/libgfortran.so.3
/usr/local/MATLAB/R2013a/sys/os/glnxa64/libgfortran.so.3.0.0

```

Now for the symbolic link

```
$ sudo ln -s /usr/lib/x86_64-linux-gnu/libgfortran.so.3 /usr/lib/x86_64-linux-gnu/libgfortran.so.1
```

Now, when trying to run the program, the following error occurs.

```
./garfield-9: symbol lookup error: ./garfield-9: undefined symbol: _gfortran_set_std

```

Does anyone have any idea how to fix this? I need to fix this problem as my professor needs a simulation ran, and none of his computers can do it so I have to use mine.

Thanks in advanced.

---

### Post by matt_symes on 2013-05-08
Hi

What version of Ubuntu are you running ?

Can you post the output of

```
cat /etc/lsb-release
```

and also

```
uname -r
```

Kind regards

---

### Post by mertinism on 2013-05-08
Sorry, should have stated those.

```
$ cat /etc/lsb-release

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
```

```
$ uname -r

3.5.0-28-generic
```

---

### Post by matt_symes on 2013-05-08
Hi

libgfortran.so.1 has been gone from Ubuntu for a long time now - pre Hardy.
```

matthew-S206:/home/matthew/garfield % ldd garfield-9
        linux-vdso.so.1 =>  (0x00007fffcbffe000)
        libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007fbb7e12b000)
        libnsl.so.1 => /lib/x86_64-linux-gnu/libnsl.so.1 (0x00007fbb7df11000)
        libcrypt.so.1 => /lib/x86_64-linux-gnu/libcrypt.so.1 (0x00007fbb7dcd7000)
        libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fbb7dad3000)
        libgslcblas.so.0 => not found
        libgsl.so.0 => not found
        libgfortran.so.1 => not found
        libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fbb7d7cd000)
        libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007fbb7d5b6000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fbb7d1ee000)
        libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007fbb7cfd0000)
        /lib64/ld-linux-x86-64.so.2 (0x00007fbb7e47f000)
        libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007fbb7cdcb000)
        libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007fbb7cbc5000)
matthew-S206:/home/matthew/garfield % 
```

```

matthew-S206:/home/matthew/garfield % apt-file search libgfortran.so.3 | wc -l
36
matthew-S206:/home/matthew/garfield % apt-file search libgfortran.so.1 | wc -l
0
matthew-S206:/home/matthew/garfield % 
```

It would seem they are incompatible.

Have you looked at building from source or building on a Linux system that has libgfortran.so.1 ?

Kind regards

---

### Post by monkeybrain2012 on 2013-05-08
Hi, NASA has apparently created some patches to address the libfortran problem. Maybe that would solve your problem.

[http://heasarc.gsfc.nasa.gov/lheasoft/linux.html](http://heasarc.gsfc.nasa.gov/lheasoft/linux.html)

---

### Post by mertinism on 2013-05-08
That fixed my problem! You and NASA have my thanks!

---

### Post by amy0520 on 2013-06-18
Hi! I have some question about installing garfield, I have sent you a message.
Thanks a lot!

---

