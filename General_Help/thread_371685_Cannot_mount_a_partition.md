---
title: "Cannot mount a partition"
date: 2007-02-27
forum: General Help
---

### Post by tomzx on 2007-02-27
I've been trying to mount one of my partitions which contains my media and here's what I'm faced with.

> root@ubuntu:/home/tom# sudo mount -t ntfs /dev/sda5 /media/sda5

mount: wrong fs type, bad option, bad superblock on /dev/hda1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

Here's what dmesg | tail gives me.
> 
root@ubuntu:/home/tom#  dmesg | tail
[17179598.236000] Bluetooth: RFCOMM TTY layer initialized
[17179598.236000] Bluetooth: RFCOMM ver 1.7
[17179600.396000] eth0: no IPv6 routers present
[17179607.356000] cdrom: hda: mrw address space DMA selected
[17179607.624000] cdrom: hda: mrw address space DMA selected
[17179607.856000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179607.976000] ISO 9660 Extensions: RRIP_1991A
[17180069.856000] cdrom: hda: mrw address space DMA selected
[17180204.604000] NTFS-fs error (device sda5): load_system_files(): Failed to load $Bitmap.
[17180204.604000] NTFS-fs error (device sda5): ntfs_fill_super(): Failed to load system files.


Here's my fdisk -l in case

> root@ubuntu:/home/tom# fdisk -l

Disque /dev/sda: 400.0 Go, 400088457216 octets
255 têtes, 63 secteurs/piste, 48641 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1        9561    76798701    7  HPFS/NTFS
/dev/sda2            9562       42113   261473940    f  W95 Etendu (LBA)
/dev/sda3           42114       48641    52436128+   7  HPFS/NTFS
/dev/sda5            9562       40676   249931206    7  HPFS/NTFS
/dev/sda6   *       40677       41982    10490413+  83  Linux
/dev/sda7           41983       42113     1052226   82  Linux swap / Solaris


---

### Post by taurus on 2007-02-27
Maybe you want to boot into XP and defrag that partition, /dev/sda5.  Then, see if you can mount it in Ubuntu this time.

---

### Post by tomzx on 2007-02-27
I am currently unable to boot into XP.

---

### Post by taurus on 2007-02-27
Does /dev/sda5 have your XP and it's corrupted; that's why you can't boot XP anymore?

What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by tomzx on 2007-02-27
as you could read from the above ;)

> root@ubuntu:/home/tom# sudo fdisk -l

Disque /dev/sda: 400.0 Go, 400088457216 octets
255 têtes, 63 secteurs/piste, 48641 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1        9561    76798701    7  HPFS/NTFS
/dev/sda2            9562       42113   261473940    f  W95 Etendu (LBA)
/dev/sda3           42114       48641    52436128+   7  HPFS/NTFS
/dev/sda5            9562       40676   249931206    7  HPFS/NTFS
/dev/sda6   *       40677       41982    10490413+  83  Linux
/dev/sda7           41983       42113     1052226   82  Linux swap / Solaris


---

### Post by taurus on 2007-02-27
Do you have XP on /dev/sda1 or /dev/sda5 because I see there are three ntfs partitions and /dev/sda1 is a bootable one so I assume XP is on /dev/sda1?  Therefore, your data/files are on /dev/sda5.

---

### Post by tomzx on 2007-02-27
well, XP is on /dev/sda1 but the boot files are messed up and if I try to boot it I get Grub Hard Disk error.

On the /dev/sda5 I have all my media files + softwares I keep (.exe), archives and some more stuff.

There's a third NTFS partition which host Vista. (/dev/sda3)

---

### Post by taurus on 2007-02-27
Can you boot Vista, /dev/sda3, and defrag /dev/sda5?

---

### Post by tomzx on 2007-02-27
No as it is the bootloader of Vista which had taken over and is currently screwed (MBR? not on the disk...)

---

### Post by tomzx on 2007-02-27
It seems I have trouble to get the partition to get mounted. 

I've looked over the net for

load_system_files(): Failed to load $Bitmap.
ntfs_fill_super(): Failed to load system files.

and found nothing that could help me fix this problem... I guess it's "unfixable".... Although, if some programmer was able to parse it, there must be a solution to the problem...

---

### Post by tre on 2007-03-07
i'm having this exact same problem!  can anyone help?

---

### Post by taurus on 2007-03-07
What problem and what's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by tre on 2007-03-08
> **taurus said:**
> What problem and what's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       25897   208017621    c  W95 FAT32 (LBA)
/dev/sda2   *       25898       30214    34676302+  83  Linux
/dev/sda3           30215       30401     1502077+   5  Extended
/dev/sda5           30215       30401     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      620181   312571192+   7  HPFS/NTFS


What I am unable to do is get Ubuntu to recognize the Windows partition on its disk /sda1/ and to recognize my second NTFS hard drive /sdb1/.
I have installed NTFS3-G.
I ran Knoppix live and it was able to recognize the partition and drive and access all files, so I am sure that the data is NOT corrupt.

I have tried to mount manually myself and through the NTFS GUI.  I get this everytime:
> mount: wrong fs type, bad option, bad superblock on /dev/hda1,
missing codepage or other error...

No luck.  Can anyone help?

---

