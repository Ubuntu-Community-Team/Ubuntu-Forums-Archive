---
title: "Propriety software in linux: Can I run Tecplot in Edgy somehow?"
date: 2006-11-23
forum: General Help
---

### Post by Castar on 2006-11-23
Hello, 

I have been trying to run tecplot 9.0 for linux in Edgy for sometime. When I try to run it, I get

MyDir/tecplot9.0/bin/mesa/tecplot.shared: relocation error: MyDir/tecplot9.0/lib/mesa/libtec.so: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference

which I can avoid by adding in the startup script

```
LD_ASSUME_KERNEL=2.4.1
export LD_ASSUME_KERNEL
```

The problem is, after I do this, I get

uname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/home/kzarog/downloads/tecplot9.0/bin/mesa/tecplot.shared: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

This is a fresh Edgy install, running the 386 kernel (generic produces the same results).  

me@mypc:~/downloads/tecplot9.0/bin$ ldd /bin/bash 
        linux-gate.so.1 =>  (0xffffe000)
        libncurses.so.5 => /lib/libncurses.so.5 (0xb7f68000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f64000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7e30000)
        /lib/ld-linux.so.2 (0xb7fb4000)
me@mypc:~/downloads/tecplot9.0/bin$ 

and 

me@mypc:tecplot9.0/bin/mesa$ ldd tecplot.shared 
        linux-gate.so.1 =>  (0xffffe000)
        libtec.so => not found
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb7f00000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7dcb000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7d02000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7cf5000)
        libXxf86vm.so.1 => /usr/lib/libXxf86vm.so.1 (0xb7cf0000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7cca000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7cb7000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7cb2000)
        libdrm.so.2 => /usr/lib/libdrm.so.2 (0xb7cab000)
        /lib/ld-linux.so.2 (0xb7f7b000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7ca8000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7ca3000)
me@mypc:tecplot9.0/bin/mesa$ 

Can someone help? It runs on Dapper! :confused:

---

### Post by autocrosser on 2006-11-23
I would say that the kernel is too new for your software--have you looked at:  [http://www.tecplot.com/products/euss/euss_main.asp](http://www.tecplot.com/products/euss/euss_main.asp)

In a Google search I found that tecplot10 was released in 2004?

If so, it would seem that you need updated software.

---

### Post by Castar on 2006-11-23
Do you know how much Tecplot costs? :D Around $1800 for a personal licence. As you can understand, trying to convince supervisors to buy it because I like Edgy more than Dapper... Well... it doesn't sound promising, does it? :D

---

### Post by autocrosser on 2006-11-23
Ouch!! I'd stay with Dapper then--that much cash is a good reason to not upgrade--you could keep Dapper for the software & dual boot Edgy for the newer stuff....

---

