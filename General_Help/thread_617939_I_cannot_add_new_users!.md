---
title: "I cannot add new users!"
date: 2007-11-19
forum: General Help
---

### Post by jdarias on 2007-11-19
Cannot do it.
I'm using the "users and groups" applet, according to the community support documentation. 
The syntoms are as follows: apparently the user is created, but if i close the applet, and reopen it, the new user is gone: it just shows root and the account created at installation.However, a group with the username is created.
The user folder inside the home folder is not created, and if i try to log in with the new user i get an error.
This is what i get trying by console:
> jdarias@familia-arias:~$ sudo adduser ares
Añadiendo usuario 'ares' ...
Agregando nuevo grupo `ares' (1001) ...
Agregando nuevo usuario `ares' (1001) con grupo `ares' ...
Creando el directorio personal '/home/ares' ...
Copiando archivos desde '/etc/skel' ...
Detenido: symlink: Permiso denegado

Removiendo directorio `/home/ares' ...
Removiendo usuario ares...
Removiendo grupo ares ...
groupdel: el grupo ares no existe
adduser: `groupdel ares' ha devuelto el código de error 6. Saliendo.

Please help!

update1: this seems to be a bug(?) [http://osdir.com/ml/debian.packages.adduser.devel/2006-03/msg00015.html](http://osdir.com/ml/debian.packages.adduser.devel/2006-03/msg00015.html)
update2: temporary workaround is to remove the symlink in the "/etc/skel" folder.

---

