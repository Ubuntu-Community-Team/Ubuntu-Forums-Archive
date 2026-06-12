---
title: "How to rename an active disk partition ?"
date: 2022-10-16
forum: General Help
---

### Post by georgesgiralt on 2022-10-16
Hello,
I've a Seagate 2TB disk. 
At first it had 4 GPT partitions, sda1 an ESP partition, sda2, sda3 windows partitions and a huge (1,8 TB ) sda4 lvm PV. 
As you may have guessed it was a disk sharing Windows and Ubuntu (20.04.5 LTS). 
I installed this huge disk on a computer with an NVME holding Windows and I suppressed the sda1, sda2, and sda3 partitions and created an sda1 partition with the exact size of the old 3 parts. This partition is an NTFS one. 
So now, fdisk report : 
```

sudo fdisk -l /dev/sda
Disque /dev/sda*: 1,84 TiB, 2000398934016*octets, 3907029168*secteurs
Disk model: ST2000LM015-2E81
Unités*: secteur de 1 × 512 = 512*octets
Taille de secteur (logique / physique)*: 512*octets / 4096*octets
taille d'E/S (minimale / optimale)*: 4096*octets / 4096*octets
Type d'étiquette de disque*: gpt
Identifiant de disque*: 4CF14399-9600-4BFE-8C03-5601D7BF20B9

Périphérique     Début        Fin   Secteurs Taille Type
/dev/sda1         2048  158820351  158818304  75,7G Données de base Microsoft
/dev/sda4    158820352 3907028991 3748208640   1,8T LVM Linux

```
Is it possible without any disruption to rename sda4 into sda2 ?
And if yes, how ? 
P.S. : This huge PV hold the whole Ubuntu system I use to post....
Thanks a lot in advance for your help and advice !

---

### Post by oldfred on 2022-10-16
Did you erase the ESP - efi system partition with Ubuntu's boot files?
Or did you reinstall grub to boot from NVMe's ESP?
You cannot boot without one or the other.

Best not to renumber partitions.
It can be done, and most things now use UUIDs, GUIDs, or labels not devices like /dev/sda4.
But anything that does still use device, will then be broken & require fixing.

---

### Post by georgesgiralt on 2022-10-16
Thank you for your answer.
The old (and erased ) ESP partition was in and for a different computer. 
The actual computer had it's own ESP part and I use this one for the ubuntu boot files (and grub) all on the NVME "disk". 
I retain that you ask me to refrain from renaming....

---

