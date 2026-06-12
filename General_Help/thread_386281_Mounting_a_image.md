---
title: "Mounting a image"
date: 2007-03-16
forum: General Help
---

### Post by tjb891 on 2007-03-16
Does anyone know if there are any programs,GUIs, or even scripts that mount and unmount image files?

---

### Post by fdrake on 2007-03-16
open terminal
sudo mkdir /mnt/image
sudo mount -o loop "image path" /mnt/image

did it work?

---

### Post by fdrake on 2007-03-16
to unmount type:
sudo umount "image path"

---

### Post by tjb891 on 2007-03-16
this was the output I got 


```
trev@trev-desktop:~$ sudo mount -o loop /home/trev/lokiinstallers/SoldierOfFortune/Soldier.Of.Fortune-Linux.iso  /mnt/image
mount: you must specify the filesystem type

```

---

### Post by taurus on 2007-03-16
```
sudo mount -t iso9660 -o loop /home/trev/lokiinstallers/SoldierOfFortune/Soldier.Of.Fortune-Linux.iso  /mnt/image
```

---

### Post by fdrake on 2007-03-16
i agree with taurus in this case it's an iso image.

---

### Post by tjb891 on 2007-03-16
you'll love this one it output this 


```
trev@trev-desktop:~$ sudo mount -t iso9660 -o loop /home/trev/lokiinstallers/SoldierOfFortune/Soldier.Of.Fortune-Linux.iso  /mnt/image

```

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by taurus on 2007-03-16
Are you sure it didn't get corrupted when you transferred it?  Try this command from a terminal.

```
file /home/trev/lokiinstallers/SoldierOfFortune/Soldier.Of.Fortune-Linux.iso
```

Otherwise, what's the output of that command from a terminal then?

```
dmesg | tail
```

---

### Post by tjb891 on 2007-03-16
/home/trev/lokiinstallers/SoldierOfFortune/Soldier.Of.Fortune-Linux.iso: data


im thinking it is a corrupted .iso file

---

### Post by fdrake on 2007-03-16
it is, it should came  the output "ISO 9660 CD-ROM filesystem data"

---

