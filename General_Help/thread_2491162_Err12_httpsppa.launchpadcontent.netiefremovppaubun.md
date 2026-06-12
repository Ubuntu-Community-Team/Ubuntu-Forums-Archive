---
title: "Err:12 https://ppa.launchpadcontent.net/iefremov/ppa/ubuntu jammy Release   404  Not"
date: 2023-09-28
forum: General Help
---

### Post by joanvillamilmd on 2023-09-28
Hola a tod@s!

Quería actualizar python a su última versión desde la terminal pero no he podido hacerlo, ya que me sale el error que aparece en el pantallazo que adjunto:

Err:12 [https://ppa.launchpadcontent.net/iefremov/ppa/ubuntu](https://ppa.launchpadcontent.net/iefremov/ppa/ubuntu) jammy Release
  404  Not Found [IP: 185.125.190.52 443]
Leyendo lista de paquetes... Hecho                        
E: El repositorio «[https://ppa.launchpadcontent.net/iefremov/ppa/ubuntu](https://ppa.launchpadcontent.net/iefremov/ppa/ubuntu) jammy Release» no tiene un fichero de Publicación.
N: No se puede actualizar de un repositorio como este de forma segura y por tanto está deshabilitado por omisión.
N: Vea la página de manual apt-secure(8) para los detalles sobre la creación de repositorios y la configuración de usuarios.

No tengo idea sobre como solucionarlo. Agradecería la ayuda de alguien, por favor. 

Gracias!

---

### Post by MAFoElffen on 2023-09-28
Why do you think you need that PPA? And it has never worked for you has it? 

Why do I say that? Because you are o 22.04, and the latest release build in that PPA was for 18.04.

I believe the PPA you are looking for is the deadsnakes PPA at: [https://launchpad.net/~deadsnakes/+archive/ubuntu/ppa](https://launchpad.net/~deadsnakes/+archive/ubuntu/ppa)

Translation to Spanish:
¿Por qué crees que necesitas ese PPA? Y nunca te ha funcionado ¿verdad?

¿Por qué digo eso? Porque tiene la versión 22.04 y la última versión de ese PPA era la 18.04.

Creo que el PPA que estás buscando es el PPA de Deadsnakes en: [https://launchpad.net/~deadsnakes/+archive/ubuntu/ppa](https://launchpad.net/~deadsnakes/+archive/ubuntu/ppa)

---

### Post by guiverc on 2023-09-28
The third party source doesn't support any release beyond 19.04/*disco*.

Did you check?  PPAs are 3rd party sources, thus all security checks are your responsibility.  A quick look at [https://launchpad.net/~iefremov/+archive/ubuntu/ppa](https://launchpad.net/~iefremov/+archive/ubuntu/ppa) should have told you it was unmaintained after 2019; thus can provide nothing good for a 2022-April release.

Sorry I only speak english, thus have answered as such.

That source should be removed (ie. *reverse of your adding it would be my suggestion*). You can delete it, comment it out (*adding a "#" to the first line of that source will disable it*), or use GUI tools if using a desktop system.

---

