---
title: "Gaim 2.0 beta 4 for dapper?"
date: 2006-10-20
forum: General Help
---

### Post by hexion on 2006-10-20
Gaim 2.0 Beta 4 is out, and it's already in edgy (not in the official repositories). Tested and several new features are wellcome :)

Anyone knows a repository to install in dapper?

---

### Post by flankker on 2006-10-20
im interesed too, can anyone help? thanx.

EDIT: i compiled it myself from source and it worked perfectly :)

---

### Post by SlugO on 2006-10-20
I built a .deb for Dapper. Get it [here]("http://ubuntuforums.org/showthread.php?t=281249").

---

### Post by hexion on 2006-10-20
> **SlugO said:**
> I built a .deb for Dapper. Get it [here]("http://ubuntuforums.org/showthread.php?t=281249").

Thanks a lot ;)

---

### Post by hexion on 2006-10-20
Mmmm... didn't work here... I paste dpkg's log:

> dpkg - atención: desactualizando gaim de 2:2.0.0beta3.1-0ubuntu1 a 1:2.0.0+beta4-1-1.
(Leyendo la base de datos ...
158506 ficheros y directorios instalados actualmente.)
Preparando para reemplazar gaim 2:2.0.0beta3.1-0ubuntu1 (usando gaim_2.0.0beta4_i386.deb) ...
Desempaquetando el reemplazo de gaim ...
dpkg: error al procesar gaim_2.0.0beta4_i386.deb (--install):
 intentando sobreescribir `/usr/share/dbus-1/services/gaim.service', que está también en el paquete gaim-data
dpkg-deb: el subproceso paste fue terminado por la señal (Tubería rota)
Se encontraron errores al procesar:
 gaim_2.0.0beta4_i386.deb



EDIT: Worked, but prior I had to remove gaim-data package :mrgreen:

---

### Post by christooss on 2006-10-26
Edgy comes with beta3.1 and not beta4

---

