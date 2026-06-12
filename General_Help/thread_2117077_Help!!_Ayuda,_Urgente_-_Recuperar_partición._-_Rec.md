---
title: "Help!! Ayuda, Urgente - Recuperar partición. - Recover partition"
date: 2013-02-17
forum: General Help
---

### Post by diegoq on 2013-02-17
Hola, 
Espero que puedan ayudarme.

Tengo dos discos duros sata, uno de 80gb y otro de 500gb.  En el disco de 80gb tenia instalado Ubuntu 11.10 y en el otro tengo toda mi data.  Formatee el disco de 80gb para hacer una instalación limpia de ubuntu 12.04, ahora viene el problema, el disco duro de 500gb no aparecía ni se montaba. Instale gparted para ver si estaba dañado o algo y vi que ahora esta como una partición SWAP.

que puedo hacer para recuperar mi data, el disco duro estaba casi lleno con toda la información de mi familia.

Agradezco su ayuda.

Datos adicionales: 
- El formateo lo hice con el disco de instalación de ubuntu12.04.

Les dejo la info del fdisk:

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros, 156301488 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x000c5b77

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *        2048   152242175    76120064   83  Linux
/dev/sda2       152244222   156301311     2028545    5  Extendida
/dev/sda5       152244224   156301311     2028544   82  Linux swap / Solaris

Disco /dev/sdb: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros, 976773168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x000e3898

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1            2048   976773119   488385536   83  Linux

---

### Post by The Cog on 2013-02-17
Google translate says:
> Hello,
Hope you can help me.

I have two SATA hard drives, a 80gb and a 500gb. The 80GB drive had installed Ubuntu 11.10 and on the other I have all my data. Format the 80GB drive to do a clean install of ubuntu 12.04, now comes the problem, 500gb hard drive did not appear nor was mounted. Install gparted to see if it was damaged or something and now saw this as a swap partition.

I can do to recover my data, the hard drive was almost full with all my family information.

I appreciate your help.

Data:
- Formatting did with the installation disc ubuntu12.04.

I leave fdisk info:

Disk / dev / sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors / track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / physical): 512 bytes / 512 bytes
Size E / S (minimum / optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c5b77

Device Boot Start End Blocks Id System
/ dev/sda1 * 2048 152242175 76120064 83 Linux
/ dev/sda2 152,244,222 156,301,311 2,028,545 5 Extended
/ dev/sda5 152,244,224 156,301,311 2,028,544 82 Linux swap / Solaris

Disk / dev / sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors / track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / physical): 512 bytes / 512 bytes
Size E / S (minimum / optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e3898

Device Boot Start End Blocks Id System
/ dev/sdb1 2048 976773119 488385536 83 Linux

---

### Post by The Cog on 2013-02-17
Just to double-check the filesystem types, please can you post the output of the command 
```
sudo blkid
```

---

### Post by diegoq on 2013-02-17
> **The Cog said:**
> Just to double-check the filesystem types, please can you post the output of the command 
```
sudo blkid
```


Here it is..

/dev/sda1: UUID="fc3a25c4-fd50-4b1d-8d34-0d275554c650" TYPE="ext4" 
/dev/sda5: UUID="9370ee98-e03a-4aee-84ff-701ea1ee9123" TYPE="swap" 
/dev/sdb1: UUID="28a23b2a-1b72-412e-b6b9-bdf3f7c78c9a" TYPE="swap"

---

### Post by The Cog on 2013-02-17
I was hoping not to see that. It looks as though it has been formatted to swap. 

I hope that because the partition is labelled as type "83 Linux" and not "82 Linux swap", your system will not be using it as swap space. the command 
```
swapon -s
```will show if it is being used. If so, use the command ```
sudo swapoff /dev/sdb1
```should stop it.

I am not sure of the best way to recover the lost data. I hope others will be able to provide better information. But if nobody else is able to help, I would suggest the following:

Install and run **testdisk** which just might be able to work out what the partition formatting used to be, and put it back again. 

If that doesn't work, there is a program called photorec that can retrieve lots of documents and photos from a formatted drive. But it gives them all numeric names and it will take you a very long time to sort through the recovered files working out what they were. I would regard this program as a last resort.

If possible, use dd to make an image of the disk on another disk first, so that you can then safely experiment with different recovery methods.

---

