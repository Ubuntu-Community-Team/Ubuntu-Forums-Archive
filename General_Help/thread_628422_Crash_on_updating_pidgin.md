---
title: "Crash on updating pidgin"
date: 2007-12-01
forum: General Help
---

### Post by g0lf0 on 2007-12-01
Hi, today i've tried to update/upgrade my system through synaptic. There are only 4 packages to update, gaim pidgin libpurple0 and pidgin-data, when i try to update them i have this error message:

E: /var/cache/apt/archives/pidgin-data_1%3a2.2.1-1ubuntu4.1_all.deb: no se puede abrir el fichero de lista de ficheros del paquete `libdjvulibre15'

and expanding it:

(Leyendo la base de datos ... dpkg: error al procesar /var/cache/apt/archives/pidgin-data_1%3a2.2.1-1ubuntu4.1_all.deb (--unpack):
 no se puede abrir el fichero de lista de ficheros del paquete `libdjvulibre15': No existe el dispositivo ó dirección
Se encontraron errores al procesar:
 /var/cache/apt/archives/pidgin-data_1%3a2.2.1-1ubuntu4.1_all.deb
Proceso detenido por haber demasiados errores.
E: Sub-process /usr/bin/dpkg returned an error code (1)
No se ha podido instalar un paquete. Intentando recuperarse:


I've tried to remove libdjvulibre15, gaim, pidgin, evince and ubuntu-desktop but the error remains.

Can anybody help me?

Thanks in advance

PD: Sorry for my english :P

---

