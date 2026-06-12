---
title: "ubuntu 12.04 linux kernel 3.2.0-80 broken dependencies"
date: 2015-04-09
forum: General Help
---

### Post by claracc on 2015-04-09
I have had a problem with the new kernel 3.2.0-80 update received this morning.

There are three packages which has been downloaded but they are not going to be updated ( I don't know why), update manager says:

Following packages have unfulfilled dependencies:

linux-headers-generic: depends on linux-headers-3.2.0-80-generic but it won't be installed
linux-headers-generic-pae:  depends on linux-headers-3.2.0-80-generic-pae  but it won't be installed
linux-image-generic: depends on linux-image-3.2.0-80-generic but it won't be installed

Running sudo apt-get install -f doesn't fix the problem, I see message there is not enough space in /usr/src/linux-headers 3.2.0-80 directory, which doesn't exist.  When I run df -h I see I have enough space in sda5 where I have installed ubuntu:

```
clara@clara1:/usr/src$ df -h
S.ficheros     Tamaño Usados  Disp Uso% Montado en
/dev/sda5         24G    12G   11G  52% /
udev             993M   4,0K  993M   1% /dev
tmpfs            201M   848K  200M   1% /run
none             5,0M      0  5,0M   0% /run/lock
none            1003M   208K 1003M   1% /run/shm
/dev/sda7         46G    23G   21G  52% /home

```

Now I am running ubuntu from the old kernel:

```
Linux clara1 3.2.0-79-generic #115-Ubuntu SMP Thu Mar 12 14:21:14 UTC 2015 i686 i686 i386 GNU/Linux

```
 My pc is a hpcompaq 6720s, running dual boot ubuntu 12.04 and win vista.

How can I fix the broken dependencies?

Thankyou very much in advance.

---

### Post by claracc on 2015-04-09
Trying to fix my problem, I run in a xterm the following command:

```
sudo apt-get --fix-broken install 
```

and here is what I obtain:

```
Leyendo lista de paquetes... Hecho 
Creando árbol de dependencias       
Leyendo la información de estado... Hecho 
Corrigiendo dependencias... Listo 
Se instalarán los siguientes paquetes extras: 
  linux-headers-3.2.0-80 linux-headers-3.2.0-80-generic 
  linux-headers-3.2.0-80-generic-pae 
Se instalarán los siguientes paquetes NUEVOS: 
  linux-headers-3.2.0-80 linux-headers-3.2.0-80-generic 
  linux-headers-3.2.0-80-generic-pae 
0 actualizados, 3 se instalarán, 0 para eliminar y 0 no actualizados. 
3 no instalados del todo o eliminados. 
Necesito descargar 13,7 MB de archivos. 
Se utilizarán 79,2 MB de espacio de disco adicional después de esta operación. 
¿Desea continuar [S/n]? s 
Des:1 http://es.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-80 all 3.2.0-80.116 [11,7 MB] 
Des:2 http://es.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-80-generic i386 3.2.0-80.116 [973 kB] 
Des:3 http://es.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-80-generic-pae i386 3.2.0-80.116 [975 kB] 
Descargados 13,7 MB en 2seg. (4.822 kB/s)                   
(Leyendo la base de datos ... 1522596 ficheros o directorios instalados actualmente.) 
Desempaquetando linux-headers-3.2.0-80 (de .../linux-headers-3.2.0-80_3.2.0-80.116_all.deb) ... 
dpkg: error al procesar /var/cache/apt/archives/linux-headers-3.2.0-80_3.2.0-80.116_all.deb (--unpack): 
 no se pudo crear `/usr/src/linux-headers-3.2.0-80/arch/arm/mach-gemini/include/mach/irqs.h.dpkg-new' (mientras se procesaba `./usr/src/linux-headers-3.2.0-80/arch/arm/mach-gemini/include/mach/irqs.h'): No queda espacio en el dispositivo 
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports» 
         dpkg-deb: error: el subproceso copiado fue terminado por la señal (Tubería rota) 
Desempaquetando linux-headers-3.2.0-80-generic (de .../linux-headers-3.2.0-80-generic_3.2.0-80.116_i386.deb) ... 
dpkg: error al procesar /var/cache/apt/archives/linux-headers-3.2.0-80-generic_3.2.0-80.116_i386.deb (--unpack): 
 error al crear el enlace simbólico `./usr/src/linux-headers-3.2.0-80-generic/include/linux/dca.h': No queda espacio en el dispositivo 
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports» 
         Desempaquetando linux-headers-3.2.0-80-generic-pae (de .../linux-headers-3.2.0-80-generic-pae_3.2.0-80.116_i386.deb) ... 
dpkg: error al procesar /var/cache/apt/archives/linux-headers-3.2.0-80-generic-pae_3.2.0-80.116_i386.deb (--unpack): 
 error al crear el enlace simbólico `./usr/src/linux-headers-3.2.0-80-generic-pae/include/linux/ide.h': No queda espacio en el dispositivo 
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports» 
         Se encontraron errores al procesar: 
 /var/cache/apt/archives/linux-headers-3.2.0-80_3.2.0-80.116_all.deb 
 /var/cache/apt/archives/linux-headers-3.2.0-80-generic_3.2.0-80.116_i386.deb 
 /var/cache/apt/archives/linux-headers-3.2.0-80-generic-pae_3.2.0-80.116_i386.deb 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

Basically, in line ```
dpkg: error al proccessing /var/cache/apt/archives/linux-headers-3.2.0-80_3.2.0-80.116_all.deb (--unpack): 
 Can not create `/usr/src/linux-headers-3.2.0-80/arch/arm/mach-gemini/include/mach/irqs.h.dpkg-new' (while proccessing `./usr/src/linux-headers-3.2.0-80/arch/arm/mach-gemini/include/mach/irqs.h'): There is not room in the device 
```

What does it mean? I have more than enough space in sda5:

```
clara@clara1:~$ df -h
S.ficheros     Tamaño Usados  Disp Uso% Montado en
/dev/sda5         24G    12G   11G  52% /
udev             993M   4,0K  993M   1% /dev
tmpfs            201M   880K  200M   1% /run
none             5,0M      0  5,0M   0% /run/lock
none            1003M   208K 1003M   1% /run/shm
/dev/sda7         46G    23G   21G  52% /home

```

What is the problem ?

---

### Post by claracc on 2015-04-09
I have found that my problem is that I am out of inodes, i.e.:

```
clara@clara1:~$ df -i
S.ficheros     Nodos-i NUsados NLibres NUso% Montado en
/dev/sda5      1569792 1562104    7688  100% /
udev            213410     532  212878    1% /dev
tmpfs           218514     475  218039    1% /run
none            218514       3  218511    1% /run/lock
none            218514       9  218505    1% /run/shm
/dev/sda7      3006464   31659 2974805    2% /home
clara@clara1:~$ dpkg --get-selections | grep linux
libselinux1					install
linux-firmware					install
linux-generic					install
linux-headers-3.2.0-30				install
linux-headers-3.2.0-30-generic			install
linux-headers-3.2.0-30-generic-pae		install
linux-headers-3.2.0-31				install
linux-headers-3.2.0-31-generic			install
linux-headers-3.2.0-31-generic-pae		install
linux-headers-3.2.0-32				install
linux-headers-3.2.0-32-generic			install
linux-headers-3.2.0-32-generic-pae		install
linux-headers-3.2.0-33				install
linux-headers-3.2.0-33-generic			install
linux-headers-3.2.0-33-generic-pae		install
linux-headers-3.2.0-34				install
linux-headers-3.2.0-34-generic			install
linux-headers-3.2.0-34-generic-pae		install
linux-headers-3.2.0-35				install
linux-headers-3.2.0-35-generic			install
linux-headers-3.2.0-35-generic-pae		install
linux-headers-3.2.0-36				install
linux-headers-3.2.0-36-generic			install
linux-headers-3.2.0-36-generic-pae		install
linux-headers-3.2.0-37				install
linux-headers-3.2.0-37-generic			install
linux-headers-3.2.0-37-generic-pae		install
linux-headers-3.2.0-38				install
linux-headers-3.2.0-38-generic			install
linux-headers-3.2.0-38-generic-pae		install
linux-headers-3.2.0-39				install
linux-headers-3.2.0-39-generic			install
linux-headers-3.2.0-39-generic-pae		install
linux-headers-3.2.0-40				install
linux-headers-3.2.0-40-generic			install
linux-headers-3.2.0-40-generic-pae		install
linux-headers-3.2.0-41				install
linux-headers-3.2.0-41-generic			install
linux-headers-3.2.0-41-generic-pae		install
linux-headers-3.2.0-43				install
linux-headers-3.2.0-43-generic			install
linux-headers-3.2.0-43-generic-pae		install
linux-headers-3.2.0-44				install
linux-headers-3.2.0-44-generic			install
linux-headers-3.2.0-44-generic-pae		install
linux-headers-3.2.0-45				install
linux-headers-3.2.0-45-generic			install
linux-headers-3.2.0-45-generic-pae		install
linux-headers-3.2.0-48				install
linux-headers-3.2.0-48-generic			install
linux-headers-3.2.0-48-generic-pae		install
linux-headers-3.2.0-49				install
linux-headers-3.2.0-49-generic			install
linux-headers-3.2.0-49-generic-pae		install
linux-headers-3.2.0-51				install
linux-headers-3.2.0-51-generic			install
linux-headers-3.2.0-51-generic-pae		install
linux-headers-3.2.0-52				install
linux-headers-3.2.0-52-generic			install
linux-headers-3.2.0-52-generic-pae		install
linux-headers-3.2.0-53				install
linux-headers-3.2.0-53-generic			install
linux-headers-3.2.0-53-generic-pae		install
linux-headers-3.2.0-54				install
linux-headers-3.2.0-54-generic			install
linux-headers-3.2.0-54-generic-pae		install
linux-headers-3.2.0-55				install
linux-headers-3.2.0-55-generic			install
linux-headers-3.2.0-55-generic-pae		install
linux-headers-3.2.0-56				install
linux-headers-3.2.0-56-generic			install
linux-headers-3.2.0-56-generic-pae		install
linux-headers-3.2.0-57				install
linux-headers-3.2.0-57-generic			install
linux-headers-3.2.0-57-generic-pae		install
linux-headers-3.2.0-58				install
linux-headers-3.2.0-58-generic			install
linux-headers-3.2.0-58-generic-pae		install
linux-headers-3.2.0-59				install
linux-headers-3.2.0-59-generic			install
linux-headers-3.2.0-59-generic-pae		install
linux-headers-3.2.0-60				install
linux-headers-3.2.0-60-generic			install
linux-headers-3.2.0-60-generic-pae		install
linux-headers-3.2.0-61				install
linux-headers-3.2.0-61-generic			install
linux-headers-3.2.0-61-generic-pae		install
linux-headers-3.2.0-63				install
linux-headers-3.2.0-63-generic			install
linux-headers-3.2.0-63-generic-pae		install
linux-headers-3.2.0-64				install
linux-headers-3.2.0-64-generic			install
linux-headers-3.2.0-64-generic-pae		install
linux-headers-3.2.0-65				install
linux-headers-3.2.0-65-generic			install
linux-headers-3.2.0-65-generic-pae		install
linux-headers-3.2.0-67				install
linux-headers-3.2.0-67-generic			install
linux-headers-3.2.0-67-generic-pae		install
linux-headers-3.2.0-68				install
linux-headers-3.2.0-68-generic			install
linux-headers-3.2.0-68-generic-pae		install
linux-headers-3.2.0-69				install
linux-headers-3.2.0-69-generic			install
linux-headers-3.2.0-69-generic-pae		install
linux-headers-3.2.0-70				install
linux-headers-3.2.0-70-generic			install
linux-headers-3.2.0-70-generic-pae		install
linux-headers-3.2.0-72				install
linux-headers-3.2.0-72-generic			install
linux-headers-3.2.0-72-generic-pae		install
linux-headers-3.2.0-73				install
linux-headers-3.2.0-73-generic			install
linux-headers-3.2.0-73-generic-pae		install
linux-headers-3.2.0-74				install
linux-headers-3.2.0-74-generic			install
linux-headers-3.2.0-74-generic-pae		install
linux-headers-3.2.0-75				install
linux-headers-3.2.0-75-generic			install
linux-headers-3.2.0-75-generic-pae		install
linux-headers-3.2.0-76				install
linux-headers-3.2.0-76-generic			install
linux-headers-3.2.0-76-generic-pae		install
linux-headers-3.2.0-77				install
linux-headers-3.2.0-77-generic			install
linux-headers-3.2.0-77-generic-pae		install
linux-headers-3.2.0-79				install
linux-headers-3.2.0-79-generic			install
linux-headers-3.2.0-79-generic-pae		install
linux-headers-generic				install
linux-headers-generic-pae			install
linux-image-3.2.0-77-generic			install
linux-image-3.2.0-79-generic			install
linux-image-3.2.0-80-generic			install
linux-image-generic				install
linux-libc-dev					install
linux-sound-base				install
pptp-linux					install
syslinux					install
syslinux-common					install
syslinux-legacy					install
util-linux					install

```

But, when I try to remove some of the linux-headers, i.e.:

```
clara@clara1:~$ sudo apt-get purge linux-headers-3.2.0-41 linux-headers-3.2.0-44 linux-headers-3.2.0-45 linux-headers-3.2.0-48
[sudo] password for clara: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Tal vez quiera ejecutar «apt-get -f install» para corregirlo:
Los siguientes paquetes tienen dependencias incumplidas:
 linux-headers-3.2.0-41-generic : Depende: linux-headers-3.2.0-41 pero no va a instalarse
 linux-headers-3.2.0-41-generic-pae : Depende: linux-headers-3.2.0-41 pero no va a instalarse
 linux-headers-3.2.0-44-generic : Depende: linux-headers-3.2.0-44 pero no va a instalarse
 linux-headers-3.2.0-44-generic-pae : Depende: linux-headers-3.2.0-44 pero no va a instalarse
 linux-headers-3.2.0-45-generic : Depende: linux-headers-3.2.0-45 pero no va a instalarse
 linux-headers-3.2.0-45-generic-pae : Depende: linux-headers-3.2.0-45 pero no va a instalarse
 linux-headers-3.2.0-48-generic : Depende: linux-headers-3.2.0-48 pero no va a instalarse
 linux-headers-3.2.0-48-generic-pae : Depende: linux-headers-3.2.0-48 pero no va a instalarse
 linux-headers-generic : Depende: linux-headers-3.2.0-80-generic pero no va a instalarse
 linux-headers-generic-pae : Depende: linux-headers-3.2.0-80-generic-pae pero no va a instalarse
E: Dependencias incumplidas. Intente «apt-get -f install» sin paquetes (o especifique una solución).

```

I cannot, ¿How can I solve the problem?, how can I recover inodes?

---

### Post by claracc on 2015-04-11
Well, at last I could solve the problem by myself. I am a little surprised about the lack of response for solving the problem. Was it an unknown problem?

As I said, the problem was I was out of inodes since I had not removed the headers of the old kernels although I had remove the old unused kernels as ubuntu's guide state: 

```
dpkg --get-selections | grep linux-image

and as the old kernels are listed, to remove them with command:

sudo apt-get remove --purge package

```

But guides don't say a word about the linux-headers wich can ocuppy a lot of space and what is worst a lot of inodes.

I has to go to /usr/src/ and there to remove some of old unused linux headers (which kernel has been removed yet) with a command similar to: sudo rm -rf linux-headers-3.2.0-35 (becarefull with -rf option) in order to recover some of the full inodes.

Once recovered some inodes, I could remove the old unused linux headers in the proper way by means of command: 

```
sudo apt-get purge linux-headers-3.2.0-41 linux-headers-3.2.0-44 linux-headers-3.2.0-45 linux-headers-3.2.0-48
```. Also I could fix the updates with command ```
sudo apt-get --fix-broken install
```

I think that when is addressed how to remove old kernels in ubuntu it had to be addressed too the way to remove the linux-headers. I think it is important to include it in documentation.

---

