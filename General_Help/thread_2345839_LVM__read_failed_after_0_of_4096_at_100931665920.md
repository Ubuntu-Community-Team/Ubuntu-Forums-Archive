---
title: "LVM : read failed after 0 of 4096 at 100931665920:"
date: 2016-12-08
forum: General Help
---

### Post by arbiel-perlacremaz on 2016-12-08
Hi

After returning from sleep mode, one of my LVM, located on a removable drive, gets unaccessible due to read errors. logical volumes get hidden for lvdisplay, blkid, mount and so on.

No error after fresh starts.

Here are the system responds to commands (parts in french do not prevent understanding)
```

remi@remi-Vostro-3550:~$ s lvdisplay -c uranie
  /dev/uranie/iconiochore: read failed after 0 of 4096 at 100931665920: Erreur d'entrée/sortie
  /dev/uranie/iconiochore: read failed after 0 of 4096 at 100931723264: Erreur d'entrée/sortie
  /dev/uranie/iconiochore: read failed after 0 of 4096 at 0: Erreur d'entrée/sortie
  /dev/uranie/iconiochore: read failed after 0 of 4096 at 4096: Erreur d'entrée/sortie
  /dev/uranie/swap: read failed after 0 of 4096 at 4294901760: Erreur d'entrée/sortie
  /dev/uranie/swap: read failed after 0 of 4096 at 4294959104: Erreur d'entrée/sortie
  /dev/uranie/swap: read failed after 0 of 4096 at 0: Erreur d'entrée/sortie
  /dev/uranie/swap: read failed after 0 of 4096 at 4096: Erreur d'entrée/sortie
  /dev/uranie/root: read failed after 0 of 4096 at 3758030848: Erreur d'entrée/sortie
  /dev/uranie/root: read failed after 0 of 4096 at 3758088192: Erreur d'entrée/sortie
  /dev/uranie/root: read failed after 0 of 4096 at 0: Erreur d'entrée/sortie
  /dev/uranie/root: read failed after 0 of 4096 at 4096: Erreur d'entrée/sortie
  /dev/uranie/home: read failed after 0 of 4096 at 3221159936: Erreur d'entrée/sortie
  /dev/uranie/home: read failed after 0 of 4096 at 3221217280: Erreur d'entrée/sortie
  /dev/uranie/home: read failed after 0 of 4096 at 0: Erreur d'entrée/sortie
  /dev/uranie/home: read failed after 0 of 4096 at 4096: Erreur d'entrée/sortie
  /dev/uranie/usr: read failed after 0 of 4096 at 5368643584: Erreur d'entrée/sortie
  /dev/uranie/usr: read failed after 0 of 4096 at 5368700928: Erreur d'entrée/sortie
  /dev/uranie/usr: read failed after 0 of 4096 at 0: Erreur d'entrée/sortie
  /dev/uranie/usr: read failed after 0 of 4096 at 4096: Erreur d'entrée/sortie
  /dev/uranie/iconiochore:uranie:3:1:-1:0:197132288:24064:-1:0:-1:252:15
  /dev/uranie/swap:uranie:3:1:-1:0:8388608:1024:-1:0:-1:252:16
  /dev/uranie/root:uranie:3:1:-1:0:7340032:896:-1:0:-1:252:17
  /dev/uranie/home:uranie:3:1:-1:0:6291456:768:-1:0:-1:252:18
  /dev/uranie/usr:uranie:3:1:-1:0:10485760:1280:-1:0:-1:252:19
remi@remi-Vostro-3550:~$

```
```


remi@remi-Vostro-3550:~$ s blkid | g uranie
remi@remi-Vostro-3550:~$ 

```

The removable device which the volume group sits on is /dev/sde2
```

remi@remi-Vostro-3550:~$ s fdisk -lu /dev/sde

Disk /dev/sde: 120.0 GB, 120034122240 bytes
255 têtes, 63 secteurs/piste, 14593 cylindres, total 234441645 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0x4c2cd691

Périphérique Amorçage  Début         Fin      Blocs    Id. Système
/dev/sde1   *        2048     4196351     2097152   83  Linux
/dev/sde2         4196352   234440703   115122176   8e  LVM Linux
remi@remi-Vostro-3550:~$ 
```

Thank you to anybody who will help me solving this issue.

Arbiel

---

