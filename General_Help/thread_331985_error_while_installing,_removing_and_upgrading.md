---
title: "error while installing, removing and upgrading"
date: 2007-01-05
forum: General Help
---

### Post by Cholito on 2007-01-05
Hi!

Today I wanted to install ffmpeg and for my sorprise I got this error: (I will try to translate the most relevant lines)

```
 alejandro@matos:~$ i ffmpeg
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
Los siguientes paquetes han sido retenidos automáticamente:
  beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings emerald 
Se han retenido los siguientes paquetes:
  beryl dbus dbus-1-utils firefox firefox-gnome-support libberylsettings0 libdbus-1-3 libemeraldengine0 libnspr4 libnss3 mozilla-thunderbird w3m 
Se instalarán los siguiente paquetes NUEVOS:
  ffmpeg 
0 paquetes actualizados, 1 nuevos instalados, 0 para eliminar y 18 sin actualizar.
Necesito descargar 0B/180kB de ficheros. Después de desempaquetar se usarán 627kB.
Escribiendo información de estado extendido... Hecho
(Reading data base ... dpkg: error while processing /var/cache/apt/archives/ffmpeg_3%3a0.cvs20060823-3.1ubuntu1_i386.deb (--unpack):
 cannot open file from `cdrecord' file list: Input/output error
Errors found while processing:
 /var/cache/apt/archives/ffmpeg_3%3a0.cvs20060823-3.1ubuntu1_i386.deb
Too many errors: process stopped 
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package could not be installed. Trying to recover: 
```

Reading the output I thought it would be a good idea to remove cdrecord and then reinstall it. When I tried to remove it I got almost the same error!

apt-get install --reinstall cdrecord didn't make anything :evil: . And it doesn't matter which package I install or if I'm upgrading, the error is always the same ](*,) 

I'm open to new ideas ;)

Saludos
Alejandro Matos

---

### Post by pseudonym on 2007-01-05
Hi, it looks like there are dependency problems ie. certain packages (or versions of packages) needed by this ffmpeg package for it to be installed, but which can't be because apt can't access them.

Did you try to install it with 'sudo dpkg -i ...'? When you do it this way, the apt package management doesn't do a dependency check, and errors like this can happen.

Unless you're 100% sure of the dependencies needed by your downloaded package, you should always install from repositories via 'sudo apt-get install ...' or Synaptic.

HTH :)

---

### Post by Cholito on 2007-01-05
I get the same cdrecord error when trying to install it with dpkg -i

The same is with dist-upgrade and apt-get install _something_ :(

---

### Post by Cholito on 2007-01-05
Even dpkg doesn't work!
please help? ](*,) 

```
alejandro@matos:~$ sudo dpkg -r opera
(Leyendo la base de datos ... dpkg: error al procesar opera (--remove):
 cannot open file from `cdrecord' file list: Input/output error
Se encontraron errores al procesar:
 opera
Proceso detenido por haber demasiados errores.
```

---

