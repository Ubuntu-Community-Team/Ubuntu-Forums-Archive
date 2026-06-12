---
title: "Error with the bbswitch-dkms"
date: 2018-05-17
forum: General Help
---

### Post by axelcagira on 2018-05-17
Hello, I may ask anybody for your help, I try everything and I don't know how to fix this problem. If anyone could help me I'll be glad. This is the error:

Status: Before uninstall, this module version was ACTIVE on this kernel.


bbswitch.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-124-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod.....(bad exit status: 135)


DKMS: uninstall completed.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error al procesar el paquete bbswitch-dkms (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 6
Se encontraron errores al procesar:
 bbswitch-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dino99 on 2018-05-17
With which process are you seeing that verbose output ?
Seems to be the false positive dpkg output when removing an old kernel (4.4.0-124 in that case)

---

### Post by axelcagira on 2018-05-17
It's happens almost everytime I try to install something. Here I let you another example, in this I wrote into the terminal "[COLOR=#24292E][FONT=SFMono-Regular]sudo apt install gdebi" And this it's what it return:

[/FONT][/COLOR]Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Los paquetes indicados a continuación se instalaron de forma automática y ya no son necesarios.
  libllvm3.8 libmircommon5 libqmi-glib1 libqpdf17 linux-headers-4.4.0-112
  linux-headers-4.4.0-112-generic linux-headers-4.4.0-116
  linux-headers-4.4.0-116-generic linux-headers-4.4.0-31
  linux-headers-4.4.0-31-generic linux-image-4.4.0-112-generic
  linux-image-4.4.0-116-generic linux-image-4.4.0-31-generic
  linux-image-extra-4.4.0-112-generic linux-image-extra-4.4.0-116-generic
  linux-image-extra-4.4.0-31-generic linux-signed-image-4.4.0-112-generic
  linux-signed-image-4.4.0-116-generic signon-plugin-password
  ubuntu-core-launcher
Utilice «sudo apt autoremove» para eliminarlos.
Se instalarán los siguientes paquetes adicionales:
  gdebi-core gksu libgksu2-0
Se instalarán los siguientes paquetes NUEVOS:
  gdebi gdebi-core gksu libgksu2-0
0 actualizados, 4 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
8 no instalados del todo o eliminados.
Se necesita descargar 157 kB de archivos.
Se utilizarán 1.181 kB de espacio de disco adicional después de esta operación.
¿Desea continuar? [S/n] S
Des:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 gdebi-core all 0.9.5.7ubuntu1 [9.716 B]
Des:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe amd64 libgksu2-0 amd64 2.0.13~pre1-6ubuntu8 [71,8 kB]
Des:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe amd64 gksu amd64 2.0.2-9ubuntu1 [51,5 kB]
Des:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe amd64 gdebi all 0.9.5.7ubuntu1 [23,6 kB]
Descargados 157 kB en 0s (455 kB/s)
Seleccionando el paquete gdebi-core previamente no seleccionado.
dpkg: aviso: falta el fichero de lista de ficheros del paquete `wine1.6-i386:i386', se supondrá que el paquete no tiene ningún fichero actualmente instalado
dpkg: aviso: falta el fichero de lista de ficheros del paquete `wine-mono0.0.8', se supondrá que el paquete no tiene ningún fichero actualmente instalado
dpkg: aviso: falta el fichero de lista de ficheros del paquete `winetricks', se supondrá que el paquete no tiene ningún fichero actualmente instalado
dpkg: aviso: falta el fichero de lista de ficheros del paquete `wine1.6', se supondrá que el paquete no tiene ningún fichero actualmente instalado
dpkg: aviso: falta el fichero de lista de ficheros del paquete `wine1.6-amd64', se supondrá que el paquete no tiene ningún fichero actualmente instalado
dpkg: aviso: falta el fichero de lista de ficheros del paquete `wine-gecko2.21:i386', se supondrá que el paquete no tiene ningún fichero actualmente instalado
dpkg: aviso: falta el fichero de lista de ficheros del paquete `wine-gecko2.21:amd64', se supondrá que el paquete no tiene ningún fichero actualmente instalado
(Leyendo la base de datos ... 401157 ficheros o directorios instalados actualmente.)
Preparando para desempaquetar .../gdebi-core_0.9.5.7ubuntu1_all.deb ...
Desempaquetando gdebi-core (0.9.5.7ubuntu1) ...
Seleccionando el paquete libgksu2-0 previamente no seleccionado.
Preparando para desempaquetar .../libgksu2-0_2.0.13~pre1-6ubuntu8_amd64.deb ...
Desempaquetando libgksu2-0 (2.0.13~pre1-6ubuntu8) ...
Seleccionando el paquete gksu previamente no seleccionado.
Preparando para desempaquetar .../gksu_2.0.2-9ubuntu1_amd64.deb ...
Desempaquetando gksu (2.0.2-9ubuntu1) ...
Seleccionando el paquete gdebi previamente no seleccionado.
Preparando para desempaquetar .../gdebi_0.9.5.7ubuntu1_all.deb ...
Desempaquetando gdebi (0.9.5.7ubuntu1) ...
Procesando disparadores para man-db (2.7.5-1) ...
Procesando disparadores para libc-bin (2.23-0ubuntu10) ...
Procesando disparadores para gconf2 (3.2.6-3ubuntu6) ...
Procesando disparadores para bamfdaemon (0.5.3~bzr0+16.04.20180209-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Procesando disparadores para desktop-file-utils (0.22-1ubuntu5.1) ...
Procesando disparadores para gnome-menus (3.13.3-6ubuntu3.1) ...
Procesando disparadores para mime-support (3.59ubuntu1) ...
Configurando bbswitch-dkms (0.8-3ubuntu1) ...
Removing old bbswitch-0.8 DKMS files...


-------- Uninstall Beginning --------
Module:  bbswitch
Version: 0.8
Kernel:  4.4.0-124-generic (x86_64)
-------------------------------------


Status: This module version was INACTIVE for this kernel.
depmod.....(bad exit status: 135)


DKMS: uninstall completed.


------------------------------
Deleting module version: 0.8
completely from the DKMS tree.
------------------------------
Done.
Loading new bbswitch-0.8 DKMS files...
First Installation: checking all kernels...
Building only for 4.4.0-124-generic
Building initial module for 4.4.0-124-generic
Done.


bbswitch:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-124-generic/updates/dkms/


depmod.....(bad exit status: 135)


-------- Uninstall Beginning --------
Module:  bbswitch
Version: 0.8
Kernel:  4.4.0-124-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


bbswitch.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-124-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod.....(bad exit status: 135)


DKMS: uninstall completed.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error al procesar el paquete bbswitch-dkms (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 6
dpkg: problemas de dependencias impiden la configuración de bumblebee:
 bumblebee depende de bbswitch-dkms | bbswitch-source; sin embargo:
 El paquete `bbswitch-dkms' no está configurado todavía.
  El paquete `bbswitch-source' no está instalado.


dpkg: error al procesar el paquete bumblebee (--configure):
 problemas de dependencias - se deja sin configurar
Configurando nvidia-340 (340.106-0ubuntu0+gpu16.04.2) ...
No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
                                           INFO:Enable nvidia-340
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
Removing old nvidia-340-340.106 DKMS files...


-------- Uninstall Beginning --------
Module:  nvidia-340
Version: 340.106
Kernel:  4.4.0-124-generic (x86_64)
-------------------------------------


Status: This module version was INACTIVE for this kernel.
depmod.....(bad exit status: 135)


DKMS: uninstall completed.


------------------------------
Deleting module version: 340.106
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-340-340.106 DKMS files...
First Installation: checking all kernels...
Building only for 4.4.0-124-generic
Building for architecture x86_64
Building initial module for 4.4.0-124-generic
Done.


nvidia_340:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-124-generic/updates/dkms/


nvidia_340_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-124-generic/updates/dkms/


depmod.....(bad exit status: 135)


-------- Uninstall Beginning --------
Module:  nvidia-340
Version: 340.106
Kernel:  4.4.0-124-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


nvidia_340.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-124-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




nvidia_340_uvm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-124-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod.....(bad exit status: 135)


DKMS: uninstall completed.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error al procesar el paquete nvidia-340 (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 6
dpkg: problemas de dependencias impiden la configuración de nvidia-340-updates:
 nvidia-340-updates depende de nvidia-340; sin embargo:
 El paquete `nvidia-340' no está configurado todavía.


dpkg: error al procesar el paquete nvidia-340-updates (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de nvidia-340-updates-uvm:
 nvidia-340-updates-uvm depende de nvidia-340-updates; sin embargo:
 El paquete `nvidia-340-updates' no está configurado todavía.


dpkg: error al procesar el paquete nvidia-340-updates-uvm (--configure):
 problemas de dependencias - se deja sin configurar
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
         No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                  dpkg: problemas de dependencias impiden la configuración de nvidia-prime:
 nvidia-prime depende de bbswitch-dkms; sin embargo:
 El paquete `bbswitch-dkms' no está configurado todavía.


dpkg: error al procesar el paquete nvidia-prime (--configure):
 problemas de dependencias - se deja sin configurar
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
         dpkg: problemas de dependencias impiden la configuración de bumblebee-nvidia:
 bumblebee-nvidia depende de bumblebee (= 3.2.1-16~gpu16.04.1); sin embargo:
 El paquete `bumblebee' no está configurado todavía.
 bumblebee-nvidia depende de nvidia-driver | nvidia-legacy-340xx-driver | nvidia-legacy-304xx-driver | nvidia-kernel-dkms | nvidia-legacy-340xx-kernel-dkms | nvidia-legacy-304xx-kernel-dkms | nvidia | nvidia-current | nvidia-current-updates | nvidia-driver-binary | nvidia-304 | nvidia-304-updates | nvidia-experimental-304 | nvidia-310 | nvidia-310-updates | nvidia-experimental-310 | nvidia-313 | nvidia-313-updates | nvidia-experimental-313 | nvidia-319 | nvidia-319-updates | nvidia-experimental-319 | nvidia-325 | nvidia-325-updates | nvidia-experimental-325 | nvidia-331 | nvidia-331-updates | nvidia-experimental-331 | nvidia-334 | nvidia-334-updates | nvidia-experimental-334 | nvidia-337 | nvidia-337-updates | nvidia-experimental-337 | nvidia-340 | nvidia-340-updates | nvidia-experimental-340 | nvidNo se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                   No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                            ia-343 |
dpkg: error al procesar el paquete bumblebee-nvidia (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de primus:
 primus depende de bumblebee; sin embargo:
 El paquete `bumblebee' no está configurado todavía.


dpkg: error al procesar el paquete primus (--configure):
 problemas de dependencias - se deja sin configurar
Configurando gdebi-core (0.9.5.7ubuntu1) ...
Configurando libgksu2-0 (2.0.13~pre1-6ubuntu8) ...
update-alternatives: utilizando /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo para proveer /usr/share/gconf/defaults/10_libgksu (libgksu-gconf-defaults) en modo automático
Procesando disparadores para gconf2 (3.2.6-3ubuntu6) ...
Configurando gksu (2.0.2-9ubuntu1) ...
Configurando gdebi (0.9.5.7ubuntu1) ...
Procesando disparadores para libc-bin (2.23-0ubuntu10) ...
Se encontraron errores al procesar:
 bbswitch-dkms
 bumblebee
 nvidia-340
 nvidia-340-updates
 nvidia-340-updates-uvm
 nvidia-prime
 bumblebee-nvidia
 primus
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

