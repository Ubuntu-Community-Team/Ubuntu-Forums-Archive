---
title: "HELP: Ubuntu Gutsy doesn't recognize pendrive"
date: 2008-03-03
forum: General Help
---

### Post by duendetuc on 2008-03-03
My ubuntu Gutsy doesn't recognize my pendrive and my mp3. And my windows does. How can I solve this?

Here is some information, all with the pendrive connected:

```
juan@juan-desktop:~$ sudo fdisk -l

Disco /dev/sda: 80.0 GB, 80000000000 bytes
255 cabezas, 63 sectores/pistas, 9726 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Disk identifier: 0x38763876

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        7415    59560956    7  HPFS/NTFS
/dev/sda2            7416        9569    17302005   83  Linux
/dev/sda3            9570        9725     1253070   82  Linux swap / Solaris

Disco /dev/hdc: 40.0 GB, 40000000000 bytes
16 cabezas, 63 sectores/pistas, 77504 cilindros
Unidades = cilindros de 1008 * 512 = 516096 bytes
Disk identifier: 0xc88ac60d

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hdc1   *           1       38752    19530976+   7  HPFS/NTFS
/dev/hdc2           38753       77504    19531008    7  HPFS/NTFS

Disco /dev/hdd: 20.0 GB, 20020396032 bytes
255 cabezas, 63 sectores/pistas, 2434 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Disk identifier: 0x002a8c25

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hdd1   *           1        2434    19551073+   7  HPFS/NTFS
```

```
juan@juan-desktop:~$ dmesg | grep usb
[   21.795692] usbcore: registered new interface driver usbfs
[   21.795714] usbcore: registered new interface driver hub
[   21.802963] usbcore: registered new device driver usb
[   21.817767] usb usb1: configuration #1 chosen from 1 choice
[   24.221752] usb usb2: configuration #1 chosen from 1 choice
```

and,

```
juan@juan-desktop:~$ dmesg | grep usb
[   21.795692] usbcore: registered new interface driver usbfs
[   21.795714] usbcore: registered new interface driver hub
[   21.802963] usbcore: registered new device driver usb
[   21.817767] usb usb1: configuration #1 chosen from 1 choice
[   24.221752] usb usb2: configuration #1 chosen from 1 choice
```


Thanks.

---

### Post by Mark_in_Hollywood on 2008-03-04
Please post the output of 

lsusb

and let's have a look.

---

### Post by duendetuc on 2008-03-04
juan@juan-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by Mark_in_Hollywood on 2008-03-06
Test the pendrive in another computer or USB reading device. Let us know what happens.

---

### Post by duendetuc on 2008-03-06
I have the same problem with my mp3 and my digital camera. I don't think that this is a device problem.

---

