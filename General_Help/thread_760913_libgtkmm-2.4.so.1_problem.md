---
title: "libgtkmm-2.4.so.1 problem"
date: 2008-04-20
forum: General Help
---

### Post by GSZX1337 on 2008-04-20
I am attempting to use an emulator front end called [Gosmose]("http://ubuntuforums.org/showthread.php?t=753863") on my desktop PC with Ubuntu 7.10 64-bit. Whenever I attempt to run it, it won't start. I get this error in the terminal.
```

error while loading shared libraries: libgtkmm-2.4.so.1: cannot open shared object file: No such file or directory

```

I search for it in Synaptic and the closest I found was libgtkmm-2.4-1c2a, so I installed it and I still get the same message. It works fine on my 32-bit Ubuntu Lappy with the same shared library installed. I even took ibgtkmm-2.4.so.1 and pasted it into every directory under usr, still no dice. And under "Installed Files", it even lists libgtkmm-2.4.so.1. Why am I still getting this error? Any help would be appreciated.

Thanks in advance,
~GSZX1337

---

### Post by GSZX1337 on 2008-04-20
G'night bump.

---

### Post by GSZX1337 on 2008-04-21
Morning bump.

---

### Post by GSZX1337 on 2008-04-22
Bumpy. Please help.

---

### Post by Cappy on 2008-04-23
Install getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

and use ```
getlibs -p libgtkmm-2.4-1c2a
```

if you are missing more libraries than just that then run getlibs on the program, e.g.
```
getlibs /usr/bin/gosmose
``` (or whatever the binary's name is) and it will take care of the rest.

---

### Post by dfreer on 2008-04-24
Try getlibs, I haven't used it myself but if it works it should save you the trouble of doing things manually. 

If you want to listen to me ramble on **alot** about how to troubleshoot your program, read on ;)

When trying to troubleshoot why a 32-bit program won't run, try running ldd on it first, like so:
```
$ ldd ./my32bitProgram
```
If successful, it should give you a list of shared libraries that your program needs to run, something like this:
```
$ ldd ./vlc
        linux-vdso.so.1 =>  (0x00007fff25ffe000)
        libvlc.so.0 => /usr/lib/libvlc.so.0 (0x00002b9a84e6a000)
        libhal.so.1 => /usr/lib/libhal.so.1 (0x00002b9a85157000)
        libdbus-1.so.3 => /usr/lib/libdbus-1.so.3 (0x00002b9a85366000)
        librt.so.1 => /lib/librt.so.1 (0x00002b9a855a3000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x00002b9a857ac000)
        libdl.so.2 => /lib/libdl.so.2 (0x00002b9a859c7000)
        libm.so.6 => /lib/libm.so.6 (0x00002b9a85bcc000)
        libc.so.6 => /lib/libc.so.6 (0x00002b9a85e4b000)
        libdvbpsi.so.4 => /usr/lib/libdvbpsi.so.4 (0x00002b9a86193000)
        libtheora.so.0 => /usr/lib/libtheora.so.0 (0x00002b9a8629f000)
        libogg.so.0 => /usr/lib/libogg.so.0 (0x00002b9a864e2000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00002b9a866e7000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00002b9a869f4000)
        /lib64/ld-linux-x86-64.so.2 (0x00002b9a84c4e000)

```

On the left hand side, you will see the name of the shared library required by this program. On the right hand side, immediately following the **=>** symbols, you will find the system path to the shared library. In the above case, I have all the libraries needed for VLC. 

Note, that was a 64-bit VLC binary. As such, it used 64-bit libraries. But when you try to run even the same program but with a 32-bit binary, you will need 32-bit libraries. Some basic 32-bit libraries come with ubuntu in the package ia32-libs (even more are provided in hardy!), all others you will need to download in some method. 

Whether you manually extract the 32-bit libraries out of 32-bit packages and dump them in your /usr/lib32/ folder (can be a pain when you want to upgrade/remove them), use getlibs, or install a specially made 64-bit package of 32-bit libraries (like ia32-libs, basically the best solution), it all ends up the same. **You just need to figure out: (1). What Libraries I need? (2). Where can I get them?**

Below is the result of running ldd on a 32-bit zsnes binary on my debian 64-bit server. Note that one library is missing:
```
$ ldd ./zsnes1.42
        linux-gate.so.1 =>  (0xffffe000)
        libz.so.1 => /usr/lib32/libz.so.1 (0xf7f8b000)
        libSDL-1.2.so.0 => /usr/lib32/libSDL-1.2.so.0 (0xf7eda000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7ec3000)
        libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf7ea0000)
        libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7e3d000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7d50000)
        libm.so.6 => /lib32/libm.so.6 (0xf7d2b000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7d1e000)
        libc.so.6 => /lib32/libc.so.6 (0xf7bd7000)
        libasound.so.2 => /usr/lib32/libasound.so.2 (0xf7b14000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7b0f000)
        libdirectfb-1.0.so.0 => /usr/lib32/libdirectfb-1.0.so.0 (0xf7aab000)
        libfusion-1.0.so.0 => /usr/lib32/libfusion-1.0.so.0 (0xf7aa3000)
        libdirect-1.0.so.0 => /usr/lib32/libdirect-1.0.so.0 (0xf7a90000)
        libvga.so.1 => /usr/lib32/libvga.so.1 (0xf7a31000)
        /lib/ld-linux.so.2 (0xf7fb4000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7944000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7936000)
        libXxf86vm.so.1 => /usr/lib32/libXxf86vm.so.1 (0xf7931000)
        libXdamage.so.1 => /usr/lib32/libXdamage.so.1 (0xf792e000)
        libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf7929000)
        libdrm.so.2 => /usr/lib32/libdrm.so.2 (0xf7920000)
        librt.so.1 => /lib32/librt.so.1 (0xf7917000)
**        libx86.so.1 => not found**
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7914000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf790f000)
```

In your case, you are missing libgtkmm-2.4.so.1. However, until you run ldd on your program (or getlibs), you won't know for sure that that's the **only** library you are missing.

Once you get a list together of what 32-bit libraries you need, I find the easiest method is to check [http://packages.ubuntu.com/](http://packages.ubuntu.com/) You can perform a search on your arch/release to see what package/s provides the libraries you need, and can even check if someone already provided a 64-bit package.

That's about it for now, but at least it gives you a starting point.

---

### Post by GSZX1337 on 2008-04-24
> **Cappy said:**
> Install getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

and use ```
getlibs -p libgtkmm-2.4-1c2a
```

if you are missing more libraries than just that then run getlibs on the program, e.g.
```
getlibs /usr/bin/gosmose
``` (or whatever the binary's name is) and it will take care of the rest.

Thanks. That did the trick. ;)

@ dfreer: Even though my problem was fixed, thank you for that trouble shooting how to. :)

---

