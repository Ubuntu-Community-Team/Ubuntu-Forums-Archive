---
title: "Help with libraries"
date: 2007-11-04
forum: General Help
---

### Post by dudds on 2007-11-04
Hi,

I am trying to run a program called dynamips on my Kubuntu Feisty laptop. When I do I get the following error message "./dynamips: error while loading shared libraries: libpcap.so.0.9.4: cannot open shared object file: No such file or directory".

However I believe I have libpcap installed as this is indicated by the Adept Manager which shows the package libpcap0.8 as installed. Also when I run the command I get the following output:
/usr/lib/libpcap.so.0.8
/usr/lib/libpcap.so.0.9.5

However when run the command ldd dynamips I get the following output:
        linux-gate.so.1 =>  (0xffffe000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f70000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7f59000)
        libpcap.so.0.9.4 => not found
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7e17000)
        /lib/ld-linux.so.2 (0xb7f85000)

Which seems to indicate to me that I need this libpcap.so.0.9.4 library, but when I try to install it via Adept Manager it's not available to install. What do I do now?

Thanks,
David

---

### Post by haldean on 2007-11-04
If you run
```
sudo ln -s /usr/lib/libpcap.so.0.9.5 /usr/lib/libpcap.so.0.9.4
```
it will create a symbolic link which points to your version of libpcap, so the program you're trying to run will find it.

---

