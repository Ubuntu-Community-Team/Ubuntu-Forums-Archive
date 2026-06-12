---
title: "firefox hates me"
date: 2007-02-03
forum: General Help
---

### Post by Roasted on 2007-02-03
Every now and then firefox randomly shuts down. Like now I just went to some Windows Vista flash video to see it, and BAM. Gone. Just like that.

This used to happen a lot with cnet.com when I wanted to watch a video on a cell phone review. It also happened before when looking at pictures on friend's web sites. 

Why?

---

### Post by taurus on 2007-02-03
Which release version you are using and which version firefox are you running?  Have on installed flash 9 plugin for your browser?

---

### Post by Roasted on 2007-02-03
I just installed Edgy on wednesday. I have whatever Firefox came with it. Flash 9 was installed via automatix2.

---

### Post by aysiu on 2007-02-03
Can you launch the command ```
firefox
``` from the terminal, go to the offending website, and then post the output (any errors) back here?

---

### Post by Roasted on 2007-02-03
jason@jason:~$ firefox
Segmentation fault (core dumped)
jason@jason:~$

---

### Post by taurus on 2007-02-03
What's the output of this command from a terminal?

```
file /usr/lib/firefox/firefox-bin
```

---

### Post by Roasted on 2007-02-03
jason@jason:~$ file /usr/lib/firefox/firefox-bin
/usr/lib/firefox/firefox-bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), for GNU/Linux 2.6.0, stripped
jason@jason:~$ 




Thanks for the help by the way. :)

---

### Post by taurus on 2007-02-03
```
ldd /usr/lib/firefox/firefox-bin
```
Are you running x86 or x86_64?

```
uname -a
```

---

### Post by Roasted on 2007-02-03
jason@jason:~$ ldd /usr/lib/firefox/firefox-bin
        linux-gate.so.1 =>  (0xffffe000)
        libmozjs.so => not found
        libxpcom.so => not found
        libxpcom_core.so => not found
        libplc4.so => /usr/lib/libplc4.so (0xb7f41000)
        libnspr4.so => /usr/lib/libnspr4.so (0xb7f0f000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7efc000)
        libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb7bac000)
        libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb7b28000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7a5e000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb797f000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb784b000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7847000)
        /lib/ld-linux.so.2 (0xb7f5a000)
        libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb7831000)
        libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb7829000)
        libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb77ee000)
        libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb77d4000)
        libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb779a000)
        libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb7796000)
        libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb7704000)
        libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb76a2000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb767b000)
        libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb764c000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb763f000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb7637000)
        libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb7634000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0xb762c000)
        libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb7628000)
        libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb761f000)
        libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb761a000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7617000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7612000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7607000)
        libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb75db000)
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb7571000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb755d000)
        librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb7554000)
        libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb7530000)
        libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb7511000)
jason@jason:~$ 





x86.

---

### Post by jolig on 2007-02-06
Hi, I am experiencing the same issue :(

firefox => coredump immediatly.

file on firefox-bin
/usr/lib/firefox/firefox-bin: ELF 64-bit LSB executable, AMD x86-64, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), for GNU/Linux 2.6.0, stripped

ldd on firefox-bin
	libmozjs.so => not found
	libxpcom.so => not found
	libxpcom_core.so => not found
	libplc4.so => /usr/lib/libplc4.so (0x00002b5d739c1000)
	libnspr4.so => /usr/lib/libnspr4.so (0x00002b5d73ac7000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00002b5d73c01000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0x00002b5d73d17000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0x00002b5d741ab000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x00002b5d74343000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00002b5d74521000)
	libc.so.6 => /lib/libc.so.6 (0x00002b5d74722000)
	libdl.so.2 => /lib/libdl.so.2 (0x00002b5d74962000)
	/lib64/ld-linux-x86-64.so.2 (0x00002b5d738a4000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x00002b5d74a66000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0x00002b5d74b7f000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0x00002b5d74c88000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0x00002b5d74dc8000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x00002b5d74ee9000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0x00002b5d7502a000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0x00002b5d7512d000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0x00002b5d752cc000)
	libm.so.6 => /lib/libm.so.6 (0x00002b5d75435000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00002b5d755b6000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00002b5d756f6000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00002b5d75807000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x00002b5d75910000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0x00002b5d75a13000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x00002b5d75b1b000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x00002b5d75c1e000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x00002b5d75d29000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00002b5d75e2e000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00002b5d75f31000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00002b5d76037000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0x00002b5d76144000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x00002b5d76272000)
	libz.so.1 => /usr/lib/libz.so.1 (0x00002b5d763ec000)
	librt.so.1 => /lib/librt.so.1 (0x00002b5d76502000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0x00002b5d7660c000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0x00002b5d76730000)

and I am running 
Linux iCore2Duo 2.6.17-10-generic #2 SMP Tue Dec 5 21:16:35 UTC 2006 x86_64 GNU/Linux

I don't know if flash 9 has been installed or not...


I tryed to trace using firefox-dbg, it seems the break is comming from libcairo...
Any Idea ?

Thanks !

---

### Post by jolig on 2007-02-08
up, nobody to help me :(

---

### Post by jolig on 2007-02-09
:-(

---

### Post by jolig on 2007-02-27
I still have the problem :(

---

