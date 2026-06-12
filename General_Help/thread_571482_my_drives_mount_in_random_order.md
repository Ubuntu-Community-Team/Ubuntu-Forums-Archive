---
title: "my drives mount in random order"
date: 2007-10-09
forum: General Help
---

### Post by traaf on 2007-10-09
hi
i have a problem with my feisty

3 hard drives
```
Disque /dev/sda: 81.9 Go, 81964302336 octets
255 têtes, 63 secteurs/piste, 9964 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1               1        1275    10241406   83  Linux
/dev/sda2            1276        1414     1116517+  82  Linux swap / Solaris
/dev/sda3            1415        8049    53295637+  83  Linux
/dev/sda4            8050        9964    15382237+  83  Linux

Disque /dev/sdb: 164.6 Go, 164696555520 octets
255 têtes, 63 secteurs/piste, 20023 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdb1   *           1        2554    20514973+   7  HPFS/NTFS
/dev/sdb2            2555       19386   135203040   83  Linux
/dev/sdb3           19387       20023     5116702+   c  W95 FAT32 (LBA)

Disque /dev/sdc: 250.0 Go, 250059350016 octets
255 têtes, 63 secteurs/piste, 30401 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdc1               1       30401   244196001   83  Linux
```

today, they appear in this order, but often changes

not a problem at boot with uuids in fstab, but I encrypted a partition and have to fill /etc/crypttab with a device adress 
curently, etc/crypttab looks like :
```
Stockage /dev/sdb1
```
i have a prompt at boot for my passphrase to mount the partition, but because of the random order of my drives, it sometimes fails to create the device mapper
i think i can not put a label or a uuid in crypttab, true ?
is there a way to make my drives always mount in the same order ?

---

### Post by thirddeep on 2007-10-09
hmmmm ... you could create a custom UDEV rule that always links to a certain point ...

Thd.

---

