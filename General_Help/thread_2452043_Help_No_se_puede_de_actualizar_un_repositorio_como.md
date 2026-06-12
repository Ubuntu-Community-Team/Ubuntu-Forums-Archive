---
title: "Help: No se puede de actualizar un repositorio como este de forma segura...."
date: 2020-10-15
forum: General Help
---

### Post by jhondavid2 on 2020-10-15
Hola. No sé nada de Ubuntu.
Estoy intentando instalar una app por la terminal pero recibo este error.
Ayuda,
Gracias

```
$ sudo add-apt-repository [https://www.mediahuman.com/packages/ubuntu](https://www.mediahuman.com/packages/ubuntu)
Obj:1 [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) focal InRelease
Obj:2 [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) focal-updates InRelease              
Obj:3 [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) focal-backports InRelease            
Obj:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease               
Ign:5 [http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu) focal InRelease        
Ign:6 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) focal InRelease          
Err:7 [http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu) focal Release          
  404  Not Found [IP: 91.189.95.83 80]
Obj:8 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) eoan InRelease                  
Err:9 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) focal Release            
  404  Not Found [IP: 91.189.95.83 80]
Des:10 [https://www.mediahuman.com/packages/ubuntu](https://www.mediahuman.com/packages/ubuntu) focal InRelease [2797 B] 
Err:10 [https://www.mediahuman.com/packages/ubuntu](https://www.mediahuman.com/packages/ubuntu) focal InRelease
  Las firmas siguientes no se pudieron verificar porque su clave pública no está disponible: NO_PUBKEY D808832C7D19F1F3
Leyendo lista de paquetes... Hecho
E: El repositorio «[http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu) focal Release» no tiene un fichero de Publicación.
N: No se puede actualizar de un repositorio como este de forma segura y por tanto está deshabilitado por omisión.
N: Vea la página de manual apt-secure(8) para los detalles sobre la creación de repositorios y la configuración de usuarios.
E: El repositorio «[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) focal Release» no tiene un fichero de Publicación.
N: No se puede actualizar de un repositorio como este de forma segura y por tanto está deshabilitado por omisión.
N: Vea la página de manual apt-secure(8) para los detalles sobre la creación de repositorios y la configuración de usuarios.
W: Error de GPG: [https://www.mediahuman.com/packages/ubuntu](https://www.mediahuman.com/packages/ubuntu) focal InRelease: Las firmas siguientes no se pudieron verificar porque su clave pública no está disponible: NO_PUBKEY D808832C7D19F1F3
E: El repositorio «[https://www.mediahuman.com/packages/ubuntu](https://www.mediahuman.com/packages/ubuntu) focal InRelease» no está firmado.
N: No se puede actualizar de un repositorio como este de forma segura y por tanto está deshabilitado por omisión.
N: Vea la página de manual apt-secure(8) para los detalles sobre la creación de repositorios y la configuración de usuarios.

$ sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 7D19F1F3
Executing: /tmp/apt-key-gpghome.z45TMfHxqs/gpg.1.sh --keyserver pgp.mit.edu --recv-keys 7D19F1F3
^C
gpg: signal Interrupt caught ... exiting
```

---

### Post by CelticWarrior on 2020-10-15
Welcome.

If you know nothing about Ubuntu, one of the first things to learn is assuring the PPAs you're adding 1) exist and 2) support your Ubuntu release.
The error messages are quite explicit. The "mediahuman" repository doesn't exist and neither of the other 3 support your release.
Remove all the repos mentioned in the error messages.

---

### Post by QIII on 2020-10-15
Hello.

You have posted in an English-speaking area of the forum.

Please edit your post and translate it into English if you are able.  If not, let us know and we will move it to one of the [local community forums]("https://ubuntuforums.org/forumdisplay.php?f=183") for native language support.

If you do translate, don't bother with the area in code tags.  Just your text.

---

