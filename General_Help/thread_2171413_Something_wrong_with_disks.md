---
title: "Something wrong with disks"
date: 2013-08-30
forum: General Help
---

### Post by martinrame on 2013-08-30
Hi, I have a machine with two 1Tb disks where I installed Ubuntu Server 12.04 a year ago. Yesterday the light went out and when it come back the machine didn't boot.

After an fsck it started to boot again, but I've found some weird studff.

First of all, here's the /etc/fstab:

```
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/pdc_ifhiicaa1 /               ext4    errors=remount-ro 0       1
/dev/mapper/pdc_ifhiicaa2 /home           ext4    defaults        0       2
/dev/mapper/pdc_ifhiicaa4 /var            ext4    defaults        0       2
/dev/mapper/pdc_ifhiicaa3 none            swap    sw              0       0
```

I don't know why there are those /dev/mapper, in other Ubuntu machines the disks are refered by UUID. 

The 2nd thing I did was using parted to show disks partitions for /dev/sda and /dev/sdb. Here are the results:

```
griensu@gpacs-gauss:~$ sudo parted /dev/sda print
Modelo: ATA ST31000524AS (scsi)
Disco /dev/sda: 1000GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. msdos

Numero  Inicio  Fin     Tamaño  Tipo     Sistema de archivos  Banderas
 1      1049kB  80,0GB  80,0GB  primary  ext4
 2      80,0GB  100GB   20,0GB  primary  ext4
 4      100GB   996GB   896GB   primary  ext4
 3      996GB   1000GB  3999MB  primary  linux-swap(v1)
```

and 

```
sudo parted /dev/sdb print
Modelo: ATA ST31000524AS (scsi)
Disco /dev/sdb: 1000GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. msdos

Numero  Inicio  Fin     Tamaño  Tipo     Sistema de archivos  Banderas
 1      1049kB  80,0GB  80,0GB  primary  ext4
 2      80,0GB  100GB   20,0GB  primary  ext4
 4      100GB   996GB   896GB   primary  ext4
 3      996GB   1000GB  3999MB  primary  linux-swap(v1)
```

As you can see, the partition type is "msdos" !!!. How can I see if this disk is mounted, and what it contains?. Also, is there a way to convert it to EXT4?.

---

### Post by btindie on 2013-08-30
The partition type of msdos is quite normal, that's the standard one. Ext4 is a filesystem, you can't use it as a partition type.

Type ```
mount
``` to list what's mounted.. and also use ```
df -h
``` to list the filesystem usage.

Going by what you have in *fstab* it looks like you're running [FakeRAID]("https://help.ubuntu.com/community/FakeRaidHowto")

---

### Post by steeldriver on 2013-08-30
The msdos refers to the *partition table* type - it's perfectly normal (although gpt partition tables have some advantages, including support for > 2TB disks). It's nothing to do with the type of the *filesystems* on the partitions themselves (which are all listed as ext4 or linux-swap, as you can see) - nothing needs to be converted.

The /dev/mapper/xxx entries usually indicate that the system is setup with LVM or RAID volumes - although there is no evidence of that on the parted outputs of your /dev/sda or /dev/sdb. Do you have other disk(s)? What is the output of

```
sudo parted -l
```

---

### Post by martinrame on 2013-08-30
Here's the output of parted -l:

```
Modelo: ATA ST31000524AS (scsi)
Disco /dev/sda: 1000GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. msdos

Numero  Inicio  Fin     Tamaño  Tipo     Sistema de archivos  Banderas
 1      1049kB  80,0GB  80,0GB  primary  ext4
 2      80,0GB  100GB   20,0GB  primary  ext4
 4      100GB   996GB   896GB   primary  ext4
 3      996GB   1000GB  3999MB  primary  linux-swap(v1)


Modelo: ATA ST31000524AS (scsi)
Disco /dev/sdb: 1000GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. msdos

Numero  Inicio  Fin     Tamaño  Tipo     Sistema de archivos  Banderas
 1      1049kB  80,0GB  80,0GB  primary  ext4
 2      80,0GB  100GB   20,0GB  primary  ext4
 4      100GB   996GB   896GB   primary  ext4
 3      996GB   1000GB  3999MB  primary  linux-swap(v1)


Modelo: Asignador de dispositivos de Linux (linear) (dm)
Disco /dev/mapper/pdc_ifhiicaa2: 20,0GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. loop

Numero  Inicio  Fin     Tamaño  Sistema de archivos  Banderas
 1      0,00B   20,0GB  20,0GB  ext4


Modelo: Asignador de dispositivos de Linux (linear) (dm)
Disco /dev/mapper/pdc_ifhiicaa4: 896GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. loop

Numero  Inicio  Fin    Tamaño  Sistema de archivos  Banderas
 1      0,00B   896GB  896GB   ext4


Modelo: Asignador de dispositivos de Linux (linear) (dm)
Disco /dev/mapper/pdc_ifhiicaa1: 80,0GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. loop

Numero  Inicio  Fin     Tamaño  Sistema de archivos  Banderas
 1      0,00B   80,0GB  80,0GB  ext4


Modelo: Asignador de dispositivos de Linux (linear) (dm)
Disco /dev/mapper/pdc_ifhiicaa3: 3999MB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. loop

Numero  Inicio  Fin     Tamaño  Sistema de archivos  Banderas
 1      0,00B   3999MB  3999MB  linux-swap(v1)


Modelo: Asignador de dispositivos de Linux (mirror) (dm)
Disco /dev/mapper/pdc_ifhiicaa: 1000GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. msdos

Numero  Inicio  Fin     Tamaño  Tipo     Sistema de archivos  Banderas
 1      1049kB  80,0GB  80,0GB  primary  ext4
 2      80,0GB  100GB   20,0GB  primary  ext4
 4      100GB   996GB   896GB   primary  ext4
 3      996GB   1000GB  3999MB  primary  linux-swap(v1)
```

---

### Post by martinrame on 2013-08-30
Does the /dev/mapper/pdc_xxxxx means I have a FakeRAID 1 composed of two 1tb disks?.

---

