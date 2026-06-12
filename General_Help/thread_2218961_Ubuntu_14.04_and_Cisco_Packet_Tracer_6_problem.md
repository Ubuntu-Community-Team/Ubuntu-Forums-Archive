---
title: "Ubuntu 14.04 and Cisco Packet Tracer 6 problem"
date: 2014-04-22
forum: General Help
---

### Post by drpaneas on 2014-04-22
drpaneas@ubuntupc:/usr/local/PacketTracer6/bin$./PacketTracer6
```
./PacketTracer6:  error while loading shared libraries: libcrypto.so.1.0.0: cannot open  shared object file: No such file or directory

```

So, let's dig the lib depedencies ....

drpaneas@ubuntupc:/usr/local/PacketTracer6/bin$ ldd ./PacketTracer6
   ```
 linux-gate.so.1 =>  (0xf76df000)
    libcrypto.so.1.0.0 => not found
    libQtWebKit.so.4 => not found
    libQtScriptTools.so.4 => not found
    libQtScript.so.4 => not found
    libQt3Support.so.4 => not found
    libQtXml.so.4 => not found
    libQtGui.so.4 => not found
    libQtNetwork.so.4 => not found
    libQtCore.so.4 => not found
    libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf769e000)
    libstdc++.so.6 => not found
    libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf7658000)
    libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf763a000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf748b000)
    /lib/ld-linux.so.2 (0xf76e0000)
```

It cannot find the libcrypto BUT .... 
```
ls /lib/libcrypto*
/lib/libcrypto.so.1.0.0
```

here there is.


Any suggestions ?

---

### Post by Burekman on 2014-04-26
Seeing as most of the libraries that were found are 32bit, you having only 64bit libraries might be the problem.

Try

```
sudo apt-get install libssl1.0.0:i386
```

to get the 32bit version of libcrypto.so.1.0.0.

Do ldd again, and if that library is now found, you will need to do the same with all the libQt dependencies as well.

Simply find the package they are part of (google is your friend), apt-get them and add :i386 at the end to get the 32bit version.

---

