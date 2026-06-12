---
title: "Can't find HD"
date: 2020-12-05
forum: General Help
---

### Post by arpeasal on 2020-12-05
I am at a complete loss.  I've gone back to a laptop I used some years ago and I've forgotten a lot of what I did with it, but I was using Xubuntu on it and I will continue with Xubuntu, after cleaning out all of the old "junk", mostly other Linux OSs I experimented with.  I remember that I replaced the original 1 TB HD with a 240 GB SSD.  Because of the problem I'll describe below, I opened the machine and confirmed there is a 240 GB SSD in the HD compartment.
 
 
 What I am at a loss about, is that there are indications that there is another HD, but I have NO IDEA where it is.  I've run Gparted and that indicates there are /dev/sda (223.57 GB) and /dev/sdb (931.51 GB).
 
 
 ```
fdisk -l shows (in part, and I'm sorry, but my system is in Portuguese, but the info is still apparent)

 Disco /dev/sda: 223,57 GiB, 240057409536 bytes, 468862128 setores

 Modelo de disco: SanDisk SDSSDA24

 Identificador do disco: 141E2F3A-632F-0347-BF20-4C952B3E3863


``` 
 
 and  
 
 
 ```
Disco /dev/sdb: 931,51 GiB, 1000204886016 bytes, 1953525168 setores

 Modelo de disco: WDC WD10SPZX-21Z  (apparently this is a Western Digital HD)

 Identificador do disco: CD1D9D26-6B2C-43E7-AB92-61BC8B0B5313


``` 
 
 On the sdb device I had an antergos and a duzero installation.  These show in Thunar as antergos and Volume de 31 GB and I can mount them and see the file structure and files in both, so apparently, the sdb device does exist on the computer, but I can't figure out where in the world it is physically located!
 
 
 Any ideas?
 
 
 Here is the complete fdisk -l output:
 
 
 ```
[randall@acer9501 ~]$ sudo fdisk -l

 Disco /dev/sda: 223,57 GiB, 240057409536 bytes, 468862128 setores
 Modelo de disco: SanDisk SDSSDA24
 Unidades: setor de 1 * 512 = 512 bytes
 Tamanho de setor (lógico/físico): 512 bytes / 512 bytes
 Tamanho E/S (mínimo/ótimo): 512 bytes / 512 bytes
 Tipo de rótulo do disco: gpt
 Identificador do disco: 141E2F3A-632F-0347-BF20-4C952B3E3863
 
 
 Dispositivo    Início       Fim   Setores Tamanho Tipo
 /dev/sda1        2048   1085439   1083392    529M Windows ambiente de recuperaçã
 /dev/sda2     1085440   1290239    204800    100M Sistema EFI
 /dev/sda3     1290240   1323007     32768     16M Microsoft reservado
 /dev/sda4     1323008 166119423 164796416   78,6G Microsoft dados básico
 /dev/sda5   166119424 168167423   2048000   1000M Sistema EFI
 /dev/sda6   168167424 364775423 196608000   93,8G Linux sistema de arquivos
 /dev/sda7   364775424 372967423   8192000    3,9G Linux swap
 /dev/sda8   372967424 468860002  95892579   45,7G Linux sistema de arquivos
 
 
 
 
 Disco /dev/sdb: 931,51 GiB, 1000204886016 bytes, 1953525168 setores
 Modelo de disco: WDC WD10SPZX-21Z
 Unidades: setor de 1 * 512 = 512 bytes
 Tamanho de setor (lógico/físico): 512 bytes / 4096 bytes
 Tamanho E/S (mínimo/ótimo): 4096 bytes / 4096 bytes
 Tipo de rótulo do disco: gpt
 Identificador do disco: CD1D9D26-6B2C-43E7-AB92-61BC8B0B5313
 
 
 Dispositivo     Início        Fim    Setores Tamanho Tipo
 /dev/sdb1         2048     206847     204800    100M Sistema EFI
 /dev/sdb2       206848     239615      32768     16M Microsoft reservado
 /dev/sdb3       239616  517826559  517586944  246,8G Microsoft dados básico
 /dev/sdb4   1951426560 1953523711    2097152      1G Windows ambiente de recuper
 /dev/sdb5    517826560  579266559   61440000   29,3G Linux sistema de arquivos
 /dev/sdb6    579266560  595650559   16384000    7,8G Linux swap
 /dev/sdb7    595650560  657090559   61440000   29,3G Linux sistema de arquivos
 /dev/sdb8    657090560 1951426559 1294336000  617,2G Linux sistema de arquivos
 
 
 Partições lógicas fora da ordem do disco.
 
 
 Disco /dev/loop0: 96,63 MiB, 101318656 bytes, 197888 setores
 Unidades: setor de 1 * 512 = 512 bytes
 Tamanho de setor (lógico/físico): 512 bytes / 512 bytes
 Tamanho E/S (mínimo/ótimo): 512 bytes / 512 bytes
 
 
 
 
 Disco /dev/loop1: 71,52 MiB, 74997760 bytes, 146480 setores
 Unidades: setor de 1 * 512 = 512 bytes
 Tamanho de setor (lógico/físico): 512 bytes / 512 bytes
 Tamanho E/S (mínimo/ótimo): 512 bytes / 512 bytes
 
 
 
 
 Disco /dev/loop2: 96,98 MiB, 101695488 bytes, 198624 setores
 Unidades: setor de 1 * 512 = 512 bytes
 Tamanho de setor (lógico/físico): 512 bytes / 512 bytes
 Tamanho E/S (mínimo/ótimo): 512 bytes / 512 bytes
 
 
 
 
 Disco /dev/loop3: 70,6 MiB, 74031104 bytes, 144592 setores
 Unidades: setor de 1 * 512 = 512 bytes
 Tamanho de setor (lógico/físico): 512 bytes / 512 bytes
 Tamanho E/S (mínimo/ótimo): 512 bytes / 512 bytes
 
 
 
 
 Disco /dev/loop4: 55,32 MiB, 58007552 bytes, 113296 setores
 Unidades: setor de 1 * 512 = 512 bytes
 Tamanho de setor (lógico/físico): 512 bytes / 512 bytes
 Tamanho E/S (mínimo/ótimo): 512 bytes / 512 bytes
 
 
 
 
 Disco /dev/loop5: 54,96 MiB, 57626624 bytes, 112552 setores
 Unidades: setor de 1 * 512 = 512 bytes
 Tamanho de setor (lógico/físico): 512 bytes / 512 bytes
 Tamanho E/S (mínimo/ótimo): 512 bytes / 512 bytes
 [randall@acer9501 ~]$
  
```

---

### Post by Autodave on 2020-12-05
Does your BIOS see the 1 tb drive?  If not, I would just go ahead and try installing on the drive that you know is there and see what happens.

---

### Post by arpeasal on 2020-12-05
I'm not 100% sure how to check if BIOS sees the 1tb drive, but on the information screen in the bios, it only lists the 240 GB SSD drive.  I didn't see any reference to any other drives on any other pages in the BIOS.

Installing is not the issue; I already have Xubuntu installed (I say Xubuntu, though, as I recall, I installed vanilla Ubuntu and then the Xubuntu desktop.).  I'm more concerned with cleaning up my Grub installation (there are about 15 lines in the menu and I really only need Ubuntu and Windows in the menu) and cleaning up the drive(s) so I know what I have and can use any free space available.

---

