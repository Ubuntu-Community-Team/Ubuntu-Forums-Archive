---
title: "jmicrovision 16.04 missing libraries"
date: 2017-01-02
forum: General Help
---

### Post by earosselot on 2017-01-02
Hello people! first i want to say that im a new user of linux, and not the best english writer, that  said ill begin with my problem:

I want to install JMicroVision ([http://www.jmicrovision.com/](http://www.jmicrovision.com/)), Im running ubuntu 16.04 amd64. 

I followed the instructions in the page:
> 
[LIST=1]
[*]Right-click on the link and select "Save Target As..."
[*]After downloading, extract the archive
[*]Then, set the execute permissions to the directory: type [COLOR=#666666][FONT=Helvetica]chmod -R u+x JMicroVision-v127-linux[/FONT][/COLOR] in a Terminal screen
[/LIST]
[COLOR=#333333][FONT=tahoma]**Uninstall:** Delete the directory of JMicroVision 1.2.7.
[/FONT][/COLOR][COLOR=#333333][FONT=tahoma]**Launch JMicroVision:** In the directory of JMicroVision 1.2.7, double-click [COLOR=#666666][FONT=Helvetica]JMVision[/FONT][/COLOR] or type [COLOR=#666666][FONT=Helvetica]./JMVision [/FONT][/COLOR]in a Terminal screen. If the launcher does not start, type [COLOR=#666666][FONT=Helvetica]ldd JMVision[/FONT][/COLOR] to show the dependencies with the shared libraries and add to your system the missing packages. It is also possible to launch JMicroVision by using the Java command (see Generic or Other Platforms Instructions).
[/FONT][/COLOR][COLOR=#333333][FONT=tahoma]**Start the Configuration Wizard: **In the directory of JMicroVision 1.2.7, type [COLOR=#666666][FONT=Helvetica]./JMVision -config [/FONT][/COLOR]in a Terminal screen.[/FONT][/COLOR]

but when i want to lauch the soft, this is the answer:
> ./JMVision: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

so, I follow the instructions and look for the libraries, and get this:
> eduardo@eduardoM6500:~/JMicroVision-v127-linux$ ldd JMVision
    linux-gate.so.1 =>  (0xf77dc000)
    libgtk-x11-2.0.so.0 => not found
    libgdk-x11-2.0.so.0 => not found
    libatk-1.0.so.0 => /usr/lib/i386-linux-gnu/libatk-1.0.so.0 (0xf778a000)
    libgdk_pixbuf-2.0.so.0 => /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0 (0xf7761000)
    libpango-1.0.so.0 => /usr/lib/i386-linux-gnu/libpango-1.0.so.0 (0xf7710000)
    libgobject-2.0.so.0 => /usr/lib/i386-linux-gnu/libgobject-2.0.so.0 (0xf76b1000)
    libgmodule-2.0.so.0 => /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0 (0xf76ac000)
    libfreetype.so.6 => /usr/lib/i386-linux-gnu/libfreetype.so.6 (0xf75fb000)
    libfontconfig.so.1 => /usr/lib/i386-linux-gnu/libfontconfig.so.1 (0xf75b2000)
    libXrender.so.1 => /usr/lib/i386-linux-gnu/libXrender.so.1 (0xf75a6000)
    libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf745b000)
    libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf7446000)
    libpng12.so.0 => /lib/i386-linux-gnu/libpng12.so.0 (0xf741a000)
    libgthread-2.0.so.0 => /usr/lib/i386-linux-gnu/libgthread-2.0.so.0 (0xf7417000)
    libglib-2.0.so.0 => /lib/i386-linux-gnu/libglib-2.0.so.0 (0xf72ee000)
    libXinerama.so.1 => /usr/lib/i386-linux-gnu/libXinerama.so.1 (0xf72ea000)
    libXxf86vm.so.1 => /usr/lib/i386-linux-gnu/libXxf86vm.so.1 (0xf72e3000)
    libpng.so.3 => not found
    libjpeg.so.62 => not found
    libexpat.so.0 => not found
    libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xf72c7000)
    libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf72c2000)
    libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xf714a000)
    libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf70f5000)
    libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf70d8000)
    libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf70bb000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf6f05000)
    libgio-2.0.so.0 => /usr/lib/i386-linux-gnu/libgio-2.0.so.0 (0xf6d3b000)
    libthai.so.0 => /usr/lib/i386-linux-gnu/libthai.so.0 (0xf6d30000)
    libffi.so.6 => /usr/lib/i386-linux-gnu/libffi.so.6 (0xf6d27000)
    libexpat.so.1 => /lib/i386-linux-gnu/libexpat.so.1 (0xf6cfd000)
    libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf6cd7000)
    libpcre.so.3 => /lib/i386-linux-gnu/libpcre.so.3 (0xf6c61000)
    /lib/ld-linux.so.2 (0x5657d000)
    libselinux.so.1 => /lib/i386-linux-gnu/libselinux.so.1 (0xf6c3b000)
    libresolv.so.2 => /lib/i386-linux-gnu/libresolv.so.2 (0xf6c22000)
    libdatrie.so.1 => /usr/lib/i386-linux-gnu/libdatrie.so.1 (0xf6c18000)
    libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf6c14000)
    libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf6c0c000)

After this, i try to look for the 'not found libraries', and try to install them, and find that the first its already intalled:
> eduardo@eduardoM6500:~$ sudo apt-get install libgtk2.0-0
[sudo] password for eduardo: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
libgtk2.0-0 ya está en su versión más reciente (2.24.30-1ubuntu1).
0 actualizados, 0 nuevos se instalarán, 0 para eliminar y 1 no actualizados.


And there is where i dont know what to do, why the program cant find the libraries? where they are? 

Thanks!

---

### Post by kevdog on 2017-01-02
I'm no expert here, but can you actually tell me the location -- I'm guessing either /usr/lib/ or /usr/local/lib of the libgtk2.0-0 library?  Also your program is looking for libgtk-x11-2.0.so.0 not just libgtk2.0-0

---

### Post by earosselot on 2017-01-02
Hi, i dont know how a library looks like, but i have found this:

4 folders:
usr/lib/x86_64-linux-gnu/libgtk2.0-0
usr/share/doc/libgtk2.0-0
usr/share/doc/libgtk2.0-0-bin
usr/share/doc/libgtk2.0-0-common

and a lot of files in var/lib/dpgk/info
all named libgtk2.0-0 with diferent extensions

and, there are 2 files:
libgtk-x11-2.0.so.0
libgtk-x11-2.0.so.0.2400.30
in usr/lib/x86_64-linux-gnu

And the last thing, acording to this: [http://packages.ubuntu.com/search?searchon=contents&keywords=libgtk-x11-2.0.so.0&mode=exactfilename&suite=yakkety&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=libgtk-x11-2.0.so.0&mode=exactfilename&suite=yakkety&arch=any)
the libgkt2.0-0 package contains libgtk-x11-2.0.so.0 library. This is the reason why im looking for the package, but yes, the program its looking for the x11.

Hope this help.
Thank you for worry !

---

### Post by earosselot on 2017-01-02
I solved it, the problem was the program was looking on i386 library folder, and the libraryes was on x64 folder.

I found the way to install i386 libraries on x64 distro. So i have do:

```
sudo apt-get install libgtk2.0-0:i386

```

and then checked the libraries with ldd, and they are good.

You opened my mind asking where the libraries are !

Thanks for helping. See you arround bud!

---

