---
title: "What else should I do to clean Boot sector?"
date: 2017-02-07
forum: General Help
---

### Post by Pablo W on 2017-02-07
Dear forum,
According to Ubuntu's software updater I have run out of space in /boot. What I have done so far to fix it is the following: 
I have run ```
sudo apt-get clean
```, ```
sudo apt-get autoclean
``` and ```
sudo apt-get autoremove
```. 

I have also deleted all but the two latest kernels, so when I run ```
dpkg --list | grep linux-headers
```

the outcome looks like this:

```
ii  linux-headers-4.4.0-57                               4.4.0-57.78                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-57-generic                       4.4.0-57.78                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-59                               4.4.0-59.80                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-59-generic                       4.4.0-59.80                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                                4.4.0.59.62                                   amd64        Generic Linux kernel headers
```

and when running ```
dpkg --list | grep linux-image
```

I get

```
ii  linux-image-4.4.0-57-generic                         4.4.0-57.78                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-59-generic                         4.4.0-59.80                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-57-generic                   4.4.0-57.78                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-59-generic                   4.4.0-59.80                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                                  4.4.0.59.62                                   amd64        Generic Linux kernel image
```

Besides, using Stacer [HTML]https://github.com/oguzhaninan/Stacer[/HTML] I have deleted apt caches, crash reports and system logs, and I have emptied the trash bin too. I guess some of these actions have nothing to do with boot, but I thought they could not harm either.

Still no space in boot. :confused:
What should I do next? 
Thank you for your help.

---

### Post by Impavidus on 2017-02-07
None of these actions did any harm (although I don't know about stacer) and the only ones that actually cleared some space in /boot were```
sudo apt-get remove linux-image-4.4.0-*
```to remove old kernels and ```
sudo apt-get autoremove
```which should have done the same.

Still not enough space on /boot? Show this:```
df
df -i
ls -l /boot
```
There is the possibility that your /boot partition is so small that it can't hold three kernels. In that case you have to remove the old one before you install the new one. Kernel images have a tendency to grow slowly. Maybe in the past it could hold three, but no longer.

---

### Post by Pablo W on 2017-02-07
Thank you, Impavidus.

This is the outcome
```
pablowains@ATIV-BOOK-9PLUS-NP940X3G-K04US:~$ df
S.ficheros                  bloques de 1K    Usados Disponibles Uso% Montado en
udev                              4018076         0     4018076   0% /dev
tmpfs                              808836     10056      798780   2% /run
/dev/mapper/ubuntu--vg-root     237578920 179264780    46222748  80% /
tmpfs                             4044172     18208     4025964   1% /dev/shm
tmpfs                                5120         4        5116   1% /run/lock
tmpfs                             4044172         0     4044172   0% /sys/fs/cgroup
/dev/sda1                          240972    132517       96014  58% /boot
cgmfs                                 100         0         100   0% /run/cgmanager/fs
tmpfs                              808836       100      808736   1% /run/user/1000
pablowains@ATIV-BOOK-9PLUS-NP940X3G-K04US:~$ df -i
S.ficheros                   Nodos-i NUsados  NLibres NUso% Montado en
udev                         1004519     564  1003955    1% /dev
tmpfs                        1011043     902  1010141    1% /run
/dev/mapper/ubuntu--vg-root 15097856  547226 14550630    4% /
tmpfs                        1011043      74  1010969    1% /dev/shm
tmpfs                        1011043       8  1011035    1% /run/lock
tmpfs                        1011043      18  1011025    1% /sys/fs/cgroup
/dev/sda1                      62248     312    61936    1% /boot
cgmfs                        1011043      14  1011029    1% /run/cgmanager/fs
tmpfs                        1011043      42  1011001    1% /run/user/1000
pablowains@ATIV-BOOK-9PLUS-NP940X3G-K04US:~$ ls -l /boot
```

I have had many kernels piling up in the past, so I guess the boot sector is not so small. My knowledge of linux is limited, though. So I could be wrong.

---

### Post by Impavidus on 2017-02-07
Your boot partition is 240972kiB in size. You currently have two kernels installed and 132517kiB in use, which is about right. You have 96014kiB left in the /boot partition, which seems about right too. That should be enough to install one more kernel – exactly one.

Can you run the software updater again? Maybe it will see now that there is enough free space. Or install the updates from command line:```
sudo apt upgrade
``` I guess you already know how to remove the 4.4.0-57 kernel if something goes wrong. Or remove the 4.4.0-57 kernel right now. Generally it's best to keep one old kernel around, in case the new one doesn't work. Sometimes a kernel gets patched without a new package, which is why we keep the old kernel even after the new one has shown to be working.

---

### Post by Pablo W on 2017-02-07
Thank you, Impavidus.

I ran the software updater again and the message was just the same: the update needed 115M and  I should free 17,1M in /boot for the update to proceed.

I then took your advice and ran ```
sudo apt upgrade
```

The outcome was```

pablowains@ATIV-BOOK-9PLUS-NP940X3G-K04US:~$ sudo apt upgrade
[sudo] password for pablowains: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Calculando la actualización... Hecho
Se instalarán los siguientes paquetes NUEVOS:
  linux-headers-4.4.0-62 linux-headers-4.4.0-62-generic
  linux-image-4.4.0-62-generic linux-image-extra-4.4.0-62-generic
Se actualizarán los siguientes paquetes:
  firefox firefox-locale-de firefox-locale-en firefox-locale-es
  firefox-locale-sv gir1.2-javascriptcoregtk-4.0 gir1.2-webkit2-4.0
  libhogweed4 libhogweed4:i386 libjavascriptcoregtk-4.0-18 libnettle6
  libnettle6:i386 libwebkit2gtk-4.0-37 libwebkit2gtk-4.0-37-gtk2 linux-generic
  linux-headers-generic linux-image-generic
17 actualizados, 4 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
Se necesita descargar 141 MB de archivos.
Se utilizarán 296 MB de espacio de disco adicional después de esta operación.
¿Desea continuar? [S/n] s
Des:1 http://ar.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libhogweed4 amd64 3.2-1ubuntu0.16.04.1 [136 kB]
Des:2 http://ar.archive.ubuntu.com/ubuntu xenial-updates/main i386 libhogweed4 i386 3.2-1ubuntu0.16.04.1 [137 kB]
Des:3 http://ar.archive.ubuntu.com/ubuntu xenial-updates/main i386 libnettle6 i386 3.2-1ubuntu0.16.04.1 [110 kB]
Des:4 http://ar.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnettle6 amd64 3.2-1ubuntu0.16.04.1 [93,5 kB]
Des:5 http://ar.archive.ubuntu.com/ubuntu xenial-updates/main amd64 firefox amd64 51.0.1+build2-0ubuntu0.16.04.2 [46,5 MB]
Des:6 http://ar.archive.ubuntu.com/ubuntu xenial-updates/main amd64 firefox-locale-de amd64 51.0.1+build2-0ubuntu0.16.04.2 [408 kB]                                           
Des:7 http://ar.archive.ubuntu.com/ubuntu xenial-updates/main amd64 firefox-locale-en amd64 51.0.1+build2-0ubuntu0.16.04.2 [636 kB]                                           
Des:8 http://ar.archive.ubuntu.com/ubuntu xenial-updates/main amd64 firefox-locale-es amd64 51.0.1+build2-0ubuntu0.16.04.2 [1.420 kB]                                         
Des:9 http://ar.archive.ubuntu.com/ubuntu xenial-updates/main amd64 firefox-locale-sv amd64 51.0.1+build2-0ubuntu0.16.04.2 [404 kB]                                           
Des:10 http://ar.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libwebkit2gtk-4.0-37-gtk2 amd64 2.14.3-0ubuntu0.16.04.1 [8.311 kB]                                       
Des:11 http://ar.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libwebkit2gtk-4.0-37 amd64 2.14.3-0ubuntu0.16.04.1 [10,2 MB]                                             
Des:12 http://ar.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libjavascriptcoregtk-4.0-18 amd64 2.14.3-0ubuntu0.16.04.1 [3.710 kB]                                     
Des:13 http://ar.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gir1.2-webkit2-4.0 amd64 2.14.3-0ubuntu0.16.04.1 [64,2 kB]                                               
Des:14 http://ar.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gir1.2-javascriptcoregtk-4.0 amd64 2.14.3-0ubuntu0.16.04.1 [22,0 kB]                                     
Des:15 http://ar.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-4.4.0-62-generic amd64 4.4.0-62.83 [21,3 MB]                                                 
Des:16 http://ar.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-extra-4.4.0-62-generic amd64 4.4.0-62.83 [36,3 MB]                                           
Des:17 http://ar.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-generic amd64 4.4.0.62.65 [1.784 B]                                                                
Des:18 http://ar.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-generic amd64 4.4.0.62.65 [2.290 B]                                                          
Des:19 http://ar.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-4.4.0-62 all 4.4.0-62.83 [9.907 kB]                                                        
Des:20 http://ar.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-4.4.0-62-generic amd64 4.4.0-62.83 [773 kB]                                                
Des:21 http://ar.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-generic amd64 4.4.0.62.65 [2.256 B]                                                        
Descargados 141 MB en 7min 43s (303 kB/s)                                                                                                                                     
(Leyendo la base de datos ... 336028 ficheros o directorios instalados actualmente.)
Preparando para desempaquetar .../libhogweed4_3.2-1ubuntu0.16.04.1_i386.deb ...
Desconfigurando libhogweed4:amd64 (3.2-1) ...
Desempaquetando libhogweed4:i386 (3.2-1ubuntu0.16.04.1) sobre (3.2-1) ...
Preparando para desempaquetar .../libhogweed4_3.2-1ubuntu0.16.04.1_amd64.deb ...
Desempaquetando libhogweed4:amd64 (3.2-1ubuntu0.16.04.1) sobre (3.2-1) ...
Preparando para desempaquetar .../libnettle6_3.2-1ubuntu0.16.04.1_amd64.deb ...
Desconfigurando libnettle6:i386 (3.2-1) ...
Desempaquetando libnettle6:amd64 (3.2-1ubuntu0.16.04.1) sobre (3.2-1) ...
Preparando para desempaquetar .../libnettle6_3.2-1ubuntu0.16.04.1_i386.deb ...
Desempaquetando libnettle6:i386 (3.2-1ubuntu0.16.04.1) sobre (3.2-1) ...
Preparando para desempaquetar .../firefox_51.0.1+build2-0ubuntu0.16.04.2_amd64.deb ...
Desempaquetando firefox (51.0.1+build2-0ubuntu0.16.04.2) sobre (51.0.1+build2-0ubuntu0.16.04.1) ...
Preparando para desempaquetar .../firefox-locale-de_51.0.1+build2-0ubuntu0.16.04.2_amd64.deb ...
Desempaquetando firefox-locale-de (51.0.1+build2-0ubuntu0.16.04.2) sobre (51.0.1+build2-0ubuntu0.16.04.1) ...
Preparando para desempaquetar .../firefox-locale-en_51.0.1+build2-0ubuntu0.16.04.2_amd64.deb ...
Desempaquetando firefox-locale-en (51.0.1+build2-0ubuntu0.16.04.2) sobre (51.0.1+build2-0ubuntu0.16.04.1) ...
Preparando para desempaquetar .../firefox-locale-es_51.0.1+build2-0ubuntu0.16.04.2_amd64.deb ...
Desempaquetando firefox-locale-es (51.0.1+build2-0ubuntu0.16.04.2) sobre (51.0.1+build2-0ubuntu0.16.04.1) ...
Preparando para desempaquetar .../firefox-locale-sv_51.0.1+build2-0ubuntu0.16.04.2_amd64.deb ...
Desempaquetando firefox-locale-sv (51.0.1+build2-0ubuntu0.16.04.2) sobre (51.0.1+build2-0ubuntu0.16.04.1) ...
Preparando para desempaquetar .../libwebkit2gtk-4.0-37-gtk2_2.14.3-0ubuntu0.16.04.1_amd64.deb ...
Desempaquetando libwebkit2gtk-4.0-37-gtk2:amd64 (2.14.3-0ubuntu0.16.04.1) sobre (2.14.2-0ubuntu0.16.04.1) ...
Preparando para desempaquetar .../libwebkit2gtk-4.0-37_2.14.3-0ubuntu0.16.04.1_amd64.deb ...
Desempaquetando libwebkit2gtk-4.0-37:amd64 (2.14.3-0ubuntu0.16.04.1) sobre (2.14.2-0ubuntu0.16.04.1) ...
Preparando para desempaquetar .../libjavascriptcoregtk-4.0-18_2.14.3-0ubuntu0.16.04.1_amd64.deb ...
Desempaquetando libjavascriptcoregtk-4.0-18:amd64 (2.14.3-0ubuntu0.16.04.1) sobre (2.14.2-0ubuntu0.16.04.1) ...
Preparando para desempaquetar .../gir1.2-webkit2-4.0_2.14.3-0ubuntu0.16.04.1_amd64.deb ...
Desempaquetando gir1.2-webkit2-4.0:amd64 (2.14.3-0ubuntu0.16.04.1) sobre (2.14.2-0ubuntu0.16.04.1) ...
Preparando para desempaquetar .../gir1.2-javascriptcoregtk-4.0_2.14.3-0ubuntu0.16.04.1_amd64.deb ...
Desempaquetando gir1.2-javascriptcoregtk-4.0:amd64 (2.14.3-0ubuntu0.16.04.1) sobre (2.14.2-0ubuntu0.16.04.1) ...
Seleccionando el paquete linux-image-4.4.0-62-generic previamente no seleccionado.
Preparando para desempaquetar .../linux-image-4.4.0-62-generic_4.4.0-62.83_amd64.deb ...
Done.
Desempaquetando linux-image-4.4.0-62-generic (4.4.0-62.83) ...
Seleccionando el paquete linux-image-extra-4.4.0-62-generic previamente no seleccionado.
Preparando para desempaquetar .../linux-image-extra-4.4.0-62-generic_4.4.0-62.83_amd64.deb ...
Desempaquetando linux-image-extra-4.4.0-62-generic (4.4.0-62.83) ...
Preparando para desempaquetar .../linux-generic_4.4.0.62.65_amd64.deb ...
Desempaquetando linux-generic (4.4.0.62.65) sobre (4.4.0.59.62) ...
Preparando para desempaquetar .../linux-image-generic_4.4.0.62.65_amd64.deb ...
Desempaquetando linux-image-generic (4.4.0.62.65) sobre (4.4.0.59.62) ...
Seleccionando el paquete linux-headers-4.4.0-62 previamente no seleccionado.
Preparando para desempaquetar .../linux-headers-4.4.0-62_4.4.0-62.83_all.deb ...
Desempaquetando linux-headers-4.4.0-62 (4.4.0-62.83) ...
Seleccionando el paquete linux-headers-4.4.0-62-generic previamente no seleccionado.
Preparando para desempaquetar .../linux-headers-4.4.0-62-generic_4.4.0-62.83_amd64.deb ...
Desempaquetando linux-headers-4.4.0-62-generic (4.4.0-62.83) ...
Preparando para desempaquetar .../linux-headers-generic_4.4.0.62.65_amd64.deb ...
Desempaquetando linux-headers-generic (4.4.0.62.65) sobre (4.4.0.59.62) ...
Procesando disparadores para libc-bin (2.23-0ubuntu5) ...
Procesando disparadores para man-db (2.7.5-1) ...
Procesando disparadores para gnome-menus (3.13.3-6ubuntu3.1) ...
Procesando disparadores para desktop-file-utils (0.22-1ubuntu5) ...
Procesando disparadores para mime-support (3.59ubuntu1) ...
Procesando disparadores para bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Configurando libnettle6:amd64 (3.2-1ubuntu0.16.04.1) ...
Configurando libnettle6:i386 (3.2-1ubuntu0.16.04.1) ...
Configurando libhogweed4:amd64 (3.2-1ubuntu0.16.04.1) ...
Configurando libhogweed4:i386 (3.2-1ubuntu0.16.04.1) ...
Configurando firefox (51.0.1+build2-0ubuntu0.16.04.2) ...
Instalando una nueva versión del fichero de configuración /etc/apparmor.d/usr.bin.firefox ...
Please restart all running instances of firefox, or you will experience problems.
Configurando firefox-locale-de (51.0.1+build2-0ubuntu0.16.04.2) ...
Configurando firefox-locale-en (51.0.1+build2-0ubuntu0.16.04.2) ...
Configurando firefox-locale-es (51.0.1+build2-0ubuntu0.16.04.2) ...
Configurando firefox-locale-sv (51.0.1+build2-0ubuntu0.16.04.2) ...
Configurando libjavascriptcoregtk-4.0-18:amd64 (2.14.3-0ubuntu0.16.04.1) ...
Configurando libwebkit2gtk-4.0-37:amd64 (2.14.3-0ubuntu0.16.04.1) ...
Configurando libwebkit2gtk-4.0-37-gtk2:amd64 (2.14.3-0ubuntu0.16.04.1) ...
Configurando gir1.2-javascriptcoregtk-4.0:amd64 (2.14.3-0ubuntu0.16.04.1) ...
Configurando gir1.2-webkit2-4.0:amd64 (2.14.3-0ubuntu0.16.04.1) ...
Configurando linux-image-4.4.0-62-generic (4.4.0-62.83) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
Generando archivo de configuración grub...
Aviso: Ya no se permite establecer GRUB_TIMEOUT a un valor distinto de cero cuando GRUB_HIDDEN_TIMEOUT está activado.
Found background image: ubuntu_kylin_grub_bg.tga
Se encontró una imagen linux: /boot/vmlinuz-4.4.0-62-generic
Se encontró una imagen initrd: /boot/initrd.img-4.4.0-62-generic
Se encontró una imagen linux: /boot/vmlinuz-4.4.0-59-generic
Se encontró una imagen initrd: /boot/initrd.img-4.4.0-59-generic
Se encontró una imagen linux: /boot/vmlinuz-4.4.0-57-generic
Se encontró una imagen initrd: /boot/initrd.img-4.4.0-57-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
hecho
Configurando linux-image-extra-4.4.0-62-generic (4.4.0-62.83) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-62-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-62-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error al procesar el paquete linux-image-extra-4.4.0-62-generic (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de linux-image-generic:
 linux-image-generic depende de linux-image-extra-4.4.0-62-generic; sin embargo:
 El paquete `linux-image-extra-4.4.0-62-generic' no está configurado todavía.

dpkg: error al procesar el paquete linux-image-generic (--configure):
 problemas de dependencias - se deja sin configurar
Configurando linux-headers-4.4.0-62 (4.4.0-62.83) ...
No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
                                                                                                                           Configurando linux-headers-4.4.0-62-generic (4.4.0-62.83) ...
Configurando linux-headers-generic (4.4.0.62.65) ...
dpkg: problemas de dependencias impiden la configuración de linux-generic:
 linux-generic depende de linux-image-generic (= 4.4.0.62.65); sin embargo:
 El paquete `linux-image-generic' no está configurado todavía.

dpkg: error al procesar el paquete linux-generic (--configure):
 problemas de dependencias - se deja sin configurar
No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
                                                                                                                           Procesando disparadores para libc-bin (2.23-0ubuntu5) ...
Se encontraron errores al procesar:
 linux-image-extra-4.4.0-62-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
pablowains@ATIV-BOOK-9PLUS-NP940X3G-K04US:~$
```

From the little I understand, the upgrade did not succeed. An Apport bug report was automatically created and I was directed to [HTML]https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/798414[/HTML]

After rebooting, I ran ```
 sudo apt-get update
``` and the outcome was
[sudo] password for pablowains: 
```
Obj:1 http://archive.canonical.com/ubuntu xenial InRelease
Obj:2 http://ar.archive.ubuntu.com/ubuntu xenial InRelease
Obj:3 http://ar.archive.ubuntu.com/ubuntu xenial-updates InRelease
Obj:4 http://ar.archive.ubuntu.com/ubuntu xenial-backports InRelease
Obj:5 http://ar.archive.ubuntu.com/ubuntu xenial-security InRelease
Leyendo lista de paquetes... Hecho
pablowains@ATIV-BOOK-9PLUS-NP940X3G-K04US:~$ sudo apt-get upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Calculando la actualización... Hecho
Los paquetes indicados a continuación se instalaron de forma automática y ya no son necesarios.
  linux-headers-4.4.0-57 linux-headers-4.4.0-57-generic
  linux-image-4.4.0-57-generic linux-image-extra-4.4.0-57-generic
Utilice «sudo apt autoremove» para eliminarlos.
0 actualizados, 0 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
3 no instalados del todo o eliminados.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
¿Desea continuar? [S/n] s
Configurando linux-image-extra-4.4.0-62-generic (4.4.0-62.83) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-62-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-62-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error al procesar el paquete linux-image-extra-4.4.0-62-generic (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de linux-image-generic:
 linux-image-generic depende de linux-image-extra-4.4.0-62-generic; sin embargo:
 El paquete `linux-image-extra-4.4.0-62-generic' no está configurado todavía.

dpkg: error al procesar el paquete linux-image-generic (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de linux-generic:
 linux-generic depende de linux-image-generic (= 4.4.0.62.65); sin embargo:
 El paquete `linux-image-generic' no está configurado todavía.

dpkg: error al procesar el paquete linux-generic (--configure):
 problemas de dependencias - se deja sin configurar
No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
                                           No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
      Se encontraron errores al procesar:
 linux-image-extra-4.4.0-62-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
pablowains@ATIV-BOOK-9PLUS-NP940X3G-K04US:~$ 

```

Assuming that I had put more strain in boot with the failed attempt, I then ran ```
sudo apt-get autoremove
``` to delete the failed upgrade, and the outcome was ```
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Los siguientes paquetes se ELIMINARÁN:
  linux-headers-4.4.0-57 linux-headers-4.4.0-57-generic linux-image-4.4.0-57-generic linux-image-extra-4.4.0-57-generic
0 actualizados, 0 nuevos se instalarán, 4 para eliminar y 0 no actualizados.
3 no instalados del todo o eliminados.
Se liberarán 296 MB después de esta operación.
¿Desea continuar? [S/n] s
(Leyendo la base de datos ... 368311 ficheros o directorios instalados actualmente.)
Desinstalando linux-headers-4.4.0-57-generic (4.4.0-57.78) ...
Desinstalando linux-headers-4.4.0-57 (4.4.0-57.78) ...
Desinstalando linux-image-extra-4.4.0-57-generic (4.4.0-57.78) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
Generando archivo de configuración grub...
Aviso: Ya no se permite establecer GRUB_TIMEOUT a un valor distinto de cero cuando GRUB_HIDDEN_TIMEOUT está activado.
Found background image: ubuntu_kylin_grub_bg.tga
Se encontró una imagen linux: /boot/vmlinuz-4.4.0-62-generic
Se encontró una imagen initrd: /boot/initrd.img-4.4.0-62-generic
Se encontró una imagen linux: /boot/vmlinuz-4.4.0-59-generic
Se encontró una imagen initrd: /boot/initrd.img-4.4.0-59-generic
Se encontró una imagen linux: /boot/vmlinuz-4.4.0-57-generic
Se encontró una imagen initrd: /boot/initrd.img-4.4.0-57-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
hecho
Desinstalando linux-image-4.4.0-57-generic (4.4.0-57.78) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-57-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
Generando archivo de configuración grub...
Aviso: Ya no se permite establecer GRUB_TIMEOUT a un valor distinto de cero cuando GRUB_HIDDEN_TIMEOUT está activado.
Found background image: ubuntu_kylin_grub_bg.tga
Se encontró una imagen linux: /boot/vmlinuz-4.4.0-62-generic
Se encontró una imagen initrd: /boot/initrd.img-4.4.0-62-generic
Se encontró una imagen linux: /boot/vmlinuz-4.4.0-59-generic
Se encontró una imagen initrd: /boot/initrd.img-4.4.0-59-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
hecho
Configurando linux-image-extra-4.4.0-62-generic (4.4.0-62.83) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
Generando archivo de configuración grub...
Aviso: Ya no se permite establecer GRUB_TIMEOUT a un valor distinto de cero cuando GRUB_HIDDEN_TIMEOUT está activado.
Found background image: ubuntu_kylin_grub_bg.tga
Se encontró una imagen linux: /boot/vmlinuz-4.4.0-62-generic
Se encontró una imagen initrd: /boot/initrd.img-4.4.0-62-generic
Se encontró una imagen linux: /boot/vmlinuz-4.4.0-59-generic
Se encontró una imagen initrd: /boot/initrd.img-4.4.0-59-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
hecho
Configurando linux-image-generic (4.4.0.62.65) ...
Configurando linux-generic (4.4.0.62.65) ...
pablowains@ATIV-BOOK-9PLUS-NP940X3G-K04US:~$ 
```

A new reboot and I ran the software updater again. To my surprise, it now reports that my system is updated. So, if I can trust it, the problem is now solved. Although I'm struggling to make sense of how has that actually happened.

---

### Post by Impavidus on 2017-02-07
I wonder why the upgrade didn't fit into the free space on /boot. I guess the install script needs some space for temporary storage. Something to keep in mind.

Anyway, the upgrade first failed, but the 4.4.0-57 packages were made autoremovable. Next you removed then, and then the upgrade succeeded.

Just be be entirely sure, check the installation status of the kernel packages:```
dpkg -l | grep -e 'linux-image\|linux-headers'
```

Next time you may want to remove the old kernel first (using apt) before running the upgrade.

---

### Post by Pablo W on 2017-02-07
Thank you, Impavidus.
Here's the outcome:

```
pablowains@ATIV-BOOK-9PLUS-NP940X3G-K04US:~$ dpkg -l | grep -e 'linux-image\|linux-headers'
ii  linux-headers-4.4.0-59                               4.4.0-59.80                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-59-generic                       4.4.0-59.80                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-62                               4.4.0-62.83                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-62-generic                       4.4.0-62.83                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                                4.4.0.62.65                                   amd64        Generic Linux kernel headers
rc  linux-image-4.4.0-57-generic                         4.4.0-57.78                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-59-generic                         4.4.0-59.80                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-62-generic                         4.4.0-62.83                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-57-generic                   4.4.0-57.78                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-59-generic                   4.4.0-59.80                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-62-generic                   4.4.0-62.83                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                                  4.4.0.62.65                                   amd64        Generic Linux kernel image
pablowains@ATIV-BOOK-9PLUS-NP940X3G-K04US:~$ 
```

---

### Post by Impavidus on 2017-02-07
That seems perfect.

---

### Post by Pablo W on 2017-02-07
Thank you, Impavidus.
Should I purge the linux-image-4.4.0-57-generic to keep it tidy?

---

### Post by ian-weisser on 2017-02-07
Best practice is to keep one older known-good kernel. A backup kernel.
You never know when a typo, a borked upgrade, malware, or other types of unforeseen causes of a very bad day will happen.
One backup kernel available to boot has saved many people, turning a very-bad-day into a mildly-annoying-hour.

It's your system, and the best choice is the one that works best for you.

---

### Post by Impavidus on 2017-02-07
> **Pablo W said:**
> Should I purge the linux-image-4.4.0-57-generic to keep it tidy?

You can purge it if you like. Right now any configuration files are still there, which would be removed by purging. But I don't think these packages have any configuration files, the the only thing cleaned is the clutter in dpkg's output.

Keep 4.4.0-59 and 4.4.0-62. When there is another upgrade and the upgrade manager again complains there's not enough space in /boot, it may be best if you first uninstall 4.4.0-59 and then install the upgrade.

---

### Post by Pablo W on 2017-02-08
Thank you Impavidus &  ian-weisser.
I'll mark the thread as solved and keep note of your comments for future upgrades.

I'm very grateful.

Cheers.

---

