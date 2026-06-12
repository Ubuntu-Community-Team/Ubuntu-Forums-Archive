---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2018-08-07
forum: General Help
---

### Post by salom2 on 2018-08-07
I am trying to use the command

```
sudo apt-get -f install
```

and it keeps returning with this error:

```
détournement de /usr/lib/i386-linux-gnu/libGL.so.1 en /usr/lib/i386-linux-gnu/libGL.so.1.distrib par nvidia-340
dpkg-divert: erreur: erreur de correspondance sur paquet
  lors de la suppression de « détournement de /usr/lib/i386-linux-gnu/libGL.so.1 par libnvidia-gl-390 »
  « détournement de /usr/lib/i386-linux-gnu/libGL.so.1 en /usr/lib/i386-linux-gnu/libGL.so.1.distrib par nvidia-340 » trouvé
dpkg: erreur de traitement de l'archive /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0~gpu18.04.1_i386.deb (--unpack) :
 new libnvidia-gl-390:i386 package pre-installation script subprocess returned error exit status 2
Préparation du dépaquetage de .../libnvidia-gl-390_390.77-0ubuntu0~gpu18.04.1_amd64.deb ...
détournement de /usr/lib/x86_64-linux-gnu/libGL.so.1 en /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib par nvidia-340
dpkg-divert: erreur: erreur de correspondance sur paquet
  lors de la suppression de « détournement de /usr/lib/x86_64-linux-gnu/libGL.so.1 par libnvidia-gl-390 »
  « détournement de /usr/lib/x86_64-linux-gnu/libGL.so.1 en /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib par nvidia-340 » trouvé
dpkg: erreur de traitement de l'archive /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0~gpu18.04.1_amd64.deb (--unpack) :
 new libnvidia-gl-390:amd64 package pre-installation script subprocess returned error exit status 2
Des erreurs ont été rencontrées pendant l'exécution :
 /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0~gpu18.04.1_i386.deb
 /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0~gpu18.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Kindly advise.

Thanks in advance

---

