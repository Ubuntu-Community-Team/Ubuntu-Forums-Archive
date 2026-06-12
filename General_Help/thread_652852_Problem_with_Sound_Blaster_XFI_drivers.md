---
title: "Problem with Sound Blaster XFI drivers"
date: 2007-12-29
forum: General Help
---

### Post by mariano.pelizzari on 2007-12-29
Hi everyone,

I'm trying to install the SoundBlaster XFI drivers and a get the following error:
I've the kernel headers and sources installed.
I'd appreciate any help.

/lib/modules/2.6.22-14-generic/build/include/linux/rwsem.h:24:65: error: asm/rwsem.h: No existe el fichero ó directorio [COLOR="Blue"](the directory or file doesn't exist or something like that, it' is in spanish)[/COLOR]
make[1]: *** [.depend] Error 1
make[1]: se sale del directorio [COLOR="Blue"](exit the directory)[/COLOR]`/opt/Creative/XFiDrv_Linux_US-1.04/src/emupia'
make: *** [emupiaclean] Error 2
Copy module files...
cp: no se puede efectuar `stat' sobre `ctossrv.o': No existe el fichero ó directorio
cp: no se puede efectuar `stat' sobre `emupia.o': No existe el fichero ó directorio
cp: no se puede efectuar `stat' sobre `ctsfman.o': No existe el fichero ó directorio
cp: no se puede efectuar `stat' sobre `haxfi.o': No existe el fichero ó directorio
cp: no se puede efectuar `stat' sobre `ctalsa.o': No existe el fichero ó directorio
cp: no se puede efectuar `stat' sobre `ct20xut.o': No existe el fichero ó directorio
cp: no se puede efectuar `stat' sobre `ctexfifx.o': No existe el fichero ó directorio
cp: no se puede efectuar `stat' sobre `cthwiut.o': No existe el fichero ó directorio
make: *** [copy_modules] Error 1
Installation Unsuccessful

The blue phrases are translation because I'm from Argetnina and my native language is Spanish.

Thks.

---

