---
title: "cannot remove libxine"
date: 2008-04-06
forum: General Help
---

### Post by watergate on 2008-04-06
I cannot remove the libxine1-gnome package since the package libperl5.8 seems to have an empty filename in it's file list.

it's in spanish the error but maybe it rings a bell for someone anyway.


root@htpc:~# apt-get autoremove
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.
  libxine1-gnome
Los siguientes paquetes se ELIMINARÁN:
  libxine1-gnome
0 actualizados, 0 se instalarán, 1 para eliminar y 72 no actualizados.
Necesito descargar 0B de archivos.
Se liberarán 77,8kB después de desempaquetar.
¿Desea continuar [S/n]? S
(Leyendo la base de datos ... dpkg: error al procesar libxine1-gnome (--remove):
 el fichero de lista de ficheros del paquete `libperl5.8'
contiene un nombre de fichero vacío
Se encontraron errores al procesar:
 libxine1-gnome
Proceso detenido por haber demasiados errores.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Partyboi2 on 2008-04-06
In a terminal try
```
sudo apt-get remove --purge libxine1-gnome
```

---

### Post by watergate on 2008-04-10
Same thing I'm afraid.

---

### Post by watergate on 2008-04-10
strangly i get this ssh information in the libperl file. I think fsck has made a mess of my filesystem
root@htpc:~# **more /var/lib/dpkg/info/libperl5.8.list**

Template: ssh/new_config
Type: boolean
Default: true
Description: Generate a new configuration file for OpenSSH?
 This version of OpenSSH has a considerably changed configuration file from

---

