---
title: "install gcc"
date: 2005-10-07
forum: General Help
---

### Post by alec_eiffel on 2005-10-07
hi everyone, I install Ubuntu like one month ago, but i realized that gcc is not installed, then, i search about how to do it in this forum, i found this command somewhere:

> sudo apt-get install build-essential

and this appears:
> 
alejadro@Lenore:~$ sudo apt-get install build-essential
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Se instalarán los siguientes paquetes extras:
  g++ g++-3.3 gcc gcc-3.3 libstdc++5-3.3-dev
Paquetes sugeridos:
  gcc-3.3-doc manpages-dev autoconf automake libtool flex bison gcc-doc
  libstdc++5-3.3-doc stl-manual
Se instalarán los siguientes paquetes NUEVOS:
  build-essential g++ g++-3.3 gcc gcc-3.3 libstdc++5-3.3-dev
0 actualizados, 6 se instalarán, 0 para eliminar y 0 no actualizados.
Se necesita descargar 0B/3116kB de archivos.
Se utilizarán 13.1MB de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? S
Cambio de medio: Por favor inserte el disco etiquetado
 'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
en la unidad '/cdrom/' y presione Intro

Cambio de medio: Por favor inserte el disco etiquetado
 'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
en la unidad '/cdrom/' y presione Intro

Cambio de medio: Por favor inserte el disco etiquetado
 'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
en la unidad '/cdrom/' y presione Intro

(Note: I am mexican, that´s the reason of the language)

everything is fine until the:

"Do you wish to continue? [S/n]"
 when I hit enter, it ask me for the disk of "Ubuntu 5.04 ... " i think that disk i the one I used to install Ubuntu, dont you?
and the disk is inside of the cd rom driver, but it dont work. 
what can I do?
There is another way tho get gcc?

---

### Post by mlomker on 2005-10-07
> There is another way tho get gcc?

Make sure that the disc is mounted before you run apt-get (click on the desktop icon and look at the contents, which will then mount it).  Alternatively you could just remove that repository from your configuration (edit the /etc/apt/sources.list and remove the first line), run apt-get update, and then download the files from the Internet when you run apt-get again.

---

### Post by alec_eiffel on 2005-10-07
thanks for the answer, well, when I put the disk on the driver, Ubuntu automatically launch a window with the content of the disk,
does it not mean that the driver is mounted?
oh, by the way, the window that ubuntu opens is "cdrom0", and the program ask for "cdrom" it's the same thing? i had just one driver.
and for the other alternative... i can´t connect Ubuntu to the internet, my modem is a winmodem, and i still dont know how to make it work.

---

### Post by mlomker on 2005-10-07
Should be the same device.  Try this:

```

sudo nano /etc/apt/sources.list

```

Find the first line that references your CD and remove it.  Ctrl-W, Y, Enter to save it.

Do this to add it back in:

```

sudo apt-cdrom add

```

---

