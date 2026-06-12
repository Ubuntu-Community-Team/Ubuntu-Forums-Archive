---
title: "edgy-backports GPG / BADSIG problem"
date: 2007-03-20
forum: General Help
---

### Post by banditti on 2007-03-20
did and apt-get update and get the following:

> W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems


Thoughts

---

### Post by banditti on 2007-03-20
I have found a dozen or so similar posts with no resolution either.

---

### Post by zvacet on 2007-03-20
Read this maybe will be helpfull to you
[http://ubuntuforums.org/showthread.php?t=90122]("http://ubuntuforums.org/showthread.php?t=90122")

---

### Post by banditti on 2007-03-21
Thanks, it "resolved itself" before I could attempt.  

When it rears its ugly head again I will give it a shot.

---

### Post by LikeVinyl on 2007-07-24
> **banditti said:**
> did and apt-get update and get the following:



Thoughts


UbuntuStudio 7.04 Ubuntu Feisty 7.04 Solución Solucion Fix Repair BADSIG 40976EAF437D05B5

Reparando sources.list Error: BADSIG 40976EAF437D05B5

Pulsar click en Aplicaciones>Accesorios>Terminal

# sudo -s

# cp /etc/apt/sources.list /home/tunombredeusuario/
# rm -f /var/lib/apt/lists/*

El sistema puede entregar el siguiente mensaje:

# rm: no se puede borrar `/var/lib/apt/lists/partial’: Es un directorio

# rm -f /var/lib/apt/lists/partial/*

# rm -f /etc/apt/*

El sistema puede informar:

# rm: no se puede borrar `/etc/apt/apt.conf.d’: Es un directorio
# rm: no se puede borrar `/etc/apt/sources.list.d’: Es un directorio

Luego en nuestro amado Gnome pulsar click sobre: Sistema>Administración>Orígenes del software>Autentificación

Pulsar click sobre el botón Restaurar valores predeterminados y luego pulsar sobre el botón Cerrar.

Regresar a la consola

Pulsar click en Aplicaciones>Accesorios>Terminal

$ sudo -s

# cp /home/tunombredeusuario/sources.list /etc/apt/

Introducir nuestro fabuloso y querido disco DVD de UbuntuStudio y teclear en la consola:

# apt-cdrom add

# apt-get update

Pasos opcionales únicamente si hemos instalado / agregado repositorios compiz-fusion y automatix desde: [http://compiz.org/Compiz_and_Compiz_Fusion_GIT_Ubuntu_Repository](http://compiz.org/Compiz_and_Compiz_Fusion_GIT_Ubuntu_Repository) y [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

# KEY=DD800CD9; gpg –keyserver subkeys.pgp.net –recv $KEY && gpg –export –armor $KEY | sudo apt-key add -

# wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)

# gpg –import automatix2.key

# gpg –export –armor E23C5FC3 | sudo apt-key add -

# apt-get update

Éxito!

Miguel Angel Ríos ::: LikeVinyl 2007 :::

Este documento puede ser reproducido o distribuido en cualquier forma sin mi permiso previo. Aunque no suponga requisito, me gustaría estar informado de su uso. Este documento se proporciona «TAL CUAL», sin garantías expresas o implícitas. Utilice la información en este documento bajo su propio riesgo.

Servidor IRC: irc.ubuntu.com

#ubuntustudio-ar

---

