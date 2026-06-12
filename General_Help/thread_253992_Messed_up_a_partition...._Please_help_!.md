---
title: "Messed up a partition.... Please help !"
date: 2006-09-09
forum: General Help
---

### Post by skaboss on 2006-09-09
Hello,

I tried today to gain some space on my second hard drive, which used to contain my old Debian install.
So i formatted the / and var partitions, and of course left /home, which contains data i want to keep.
Did it with qtParted. The problem is i can't access the data on this drive anymore.

```

sudo mount /dev/hdb6 /media/debian -t ext3
mount: type erroné de système de fichiers, option erronée, super bloc erroné sur /dev/hdb6,
       codepage manquante ou autre erreur
       Dans quelques cas certaines informations sont utiles dans syslog - essayez
       dmesg | tail  ou quelque chose du genre

```
Sorry, it's in french, but means something like wrong system file, bad super block...

Here is what fdisk -l says : 
```

Disque /dev/hdb: 60.0 Go, 60022480896 octets
255 têtes, 63 secteurs/piste, 7297 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hdb1   *           1          34      273073+  83  Linux
/dev/hdb2              35        7297    58340047+   f  W95 Etendu (LBA)
/dev/hdb5            1245        7297    48620691   83  Linux
/dev/hdb6              35        1244     9719262   83  Linux

Les entrées de la table de partitions ne sont pas dans l'ordre du disque


```

The partition  i need to mount (/dev/hdb6) have always been ext3...
Can somebody help me please, i would like so much to get my data back !!

---

### Post by orb9220 on 2006-09-09
repost this in installing and upgrading and you will get more help there.

---

### Post by skaboss on 2006-09-10
Ok, thank you. I copied my thread to the installation / update forum (i didn't fint out how to delete this one).

---

