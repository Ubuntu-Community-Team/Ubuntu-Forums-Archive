---
title: "strange problem on my desktop"
date: 2017-05-26
forum: General Help
---

### Post by hilario_ferreira on 2017-05-26
Hello everybody:

I have a strange problem on my desktop that I would like to share with you so that maybe someone can have an explanation or a solution:

I have on my desktop a dual boot system - main boot is ubuntu 14.04 LTS second option is windows 10 (both 64 bits)
I have 3 HD - 1 with ubuntu installed (1 tb ) another with windows installed (1 tb) and a third one with 2 tb where I have all my media (movies , music etc..)
-From ubuntu I can access the media HD and play the files - I don't know why on the ubuntu launcher the media disk is described as "NEW VOLUME" when the other disks are described as: volume with xxx mb !!!
-From windows I can't acces the media HD !!!

Another problem: I use plex media server to watch all my media,  but inside ubuntu I can't set that  HD as my media because I can't give the path to the disk on plex server.

Does anyone  understand why this is happening ???

---

### Post by howefield on 2017-05-26
> **hilario_ferreira said:**
> -From windows I can't acces the media HD !!!

This would often be because the disk/partition is formatted with a file system unknown to Windows, eg ext3 or ext4. How is the media disk formatted ?

---

### Post by vasa1 on 2017-05-26
Would running```
sudo fdisk -l
```provide a clue?

---

### Post by hilario_ferreira on 2017-05-26
> **howefield said:**
> This would often be because the disk/partition is formatted with a file system unknown to Windows, eg ext3 or ext4. How is the media disk formatted ?

I don't know how it is formatted but this media disk was used once by windows with the same purpose, and I didn't change anything since then !!

> **vasa1 said:**
> Would running```
sudo fdisk -l
```provide a clue?

?????????

```
fdisk: opção inválida -- '1'
Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>             sector size (512, 1024, 2048 or 4096)
 -c[=<mode>]           compatible mode: 'dos' or 'nondos' (default)
 -h                    print this help text
 -u[=<unit>]           display units: 'cylinders' or 'sectors' (default)
 -v                    print program version
 -C <number>           specify the number of cylinders
 -H <number>           specify the number of heads
 -S <number>           specify the number of sectors per track
```

---

### Post by howefield on 2017-05-26
> **hilario_ferreira said:**
> fdisk: opção inválida -- '1'

The command doesn't use the number 1, it is a lower case letter l

---

### Post by hilario_ferreira on 2017-05-26
> **howefield said:**
> The command doesn't use the number 1, it is a lower case letter l

Sorry my mistake.

Here it is:

```
Disco /dev/sda: 1000.2 GB, 1000204886016 bytes
255 cabeças, 63 setores/trilhas, 121601 cilindros, total de 1953525168 setores
Unidades = setores de 1 * 512 = 512 bytes
Tamanho do setor (lógico/físico): 512 bytes / 4096 bytes
Tamanho da E/S (mínimo/ideal): 4096 bytes / 4096 bytes
Identificador do disco: 0x98b36e55

Dispositivo Boot      Início        Fim      Blocos   Id  Sistema
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   206579711   103186432    7  HPFS/NTFS/exFAT
/dev/sda3       206579712  1953521117   873470703    7  HPFS/NTFS/exFAT

AVISO: GPT (Tabela de Partição GUID) detectada em '/dev/sdb'! O utilitário fdisk não tem suporte para GPT. Utilize o GNU Parted.


Disco /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 cabeças, 63 setores/trilhas, 243201 cilindros, total de 3907029168 setores
Unidades = setores de 1 * 512 = 512 bytes
Tamanho do setor (lógico/físico): 512 bytes / 512 bytes
Tamanho da E/S (mínimo/ideal): 512 bytes / 512 bytes
Identificador do disco: 0x00000000

Dispositivo Boot      Início        Fim      Blocos   Id  Sistema
/dev/sdb1               1  3907029167  1953514583+  ee  GPT

Disco /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 cabeças, 63 setores/trilhas, 121601 cilindros, total de 1953525168 setores
Unidades = setores de 1 * 512 = 512 bytes
Tamanho do setor (lógico/físico): 512 bytes / 512 bytes
Tamanho da E/S (mínimo/ideal): 512 bytes / 512 bytes
Identificador do disco: 0xc144b16f

Dispositivo Boot      Início        Fim      Blocos   Id  Sistema
/dev/sdc1            2048  1947252735   973625344   83  Linux
/dev/sdc2      1947254782  1953523711     3134465    5  Estendida
/dev/sdc5      1947254784  1953523711     3134464   82  Linux swap / Solaris
```

here's another strange thing that I noticed:

If I copy some files from the media disk, place them on another folder inside ubuntu and if I go to plex server and indicate that folder as my media folder , plex scans the folder and tells me 
that there are no media on that folder !!! however I can play those files using VLC !!!

---

### Post by howefield on 2017-05-26
With it being a GPT disk try..

```
sudo gdisk -l /dev/sdb
```

what is the output ?

---

### Post by hilario_ferreira on 2017-05-26
> **howefield said:**
> With it being a GPT disk try..

```
sudo gdisk -l /dev/sdb
```

what is the output ?


```
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 3907029168 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 63F838F7-82F6-11E0-9417-001F1F71F5A3
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2157 sectors (1.1 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      3907028991   1.8 TiB     EF01  Basic data partition
```

---

### Post by slickymaster on 2017-05-26
@hilario_ferreira

Please[ use code tags when posting output code]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168"). Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The use of code tags makes the post clean, compact and more appealing, thus getting more attention from readers.

---

