---
title: "Howto reactivate HDD"
date: 2016-05-22
forum: General Help
---

### Post by greenshirt11 on 2016-05-22
Hi,

My system:
- GPT
- SSD boot drive with Win8 + Ubuntu 14.04 (/dev/sda)
- HDD drive containing Win + Linux (ext2) partitions (/dev/sdb)

The HDD used to be bootable too but for some unknown reason has lost the MBR info.
Windows does not see the drive; from Ubuntu when I start gparted it comes with a message box:
- /dev/sdb containing GPT signatures.
- not valid fake msdos partition table
- Is this a GPT drive?
So I click 'yes' and gparted shows start and end of partitions with type (NTFS etc).

What can I do to make the HDD usable again (on Ubuntu and Windows) without losing the data already on it?
Is that possible at all?

Thanks for any suggestions.

F

---

### Post by oldfred on 2016-05-22
Issue is whether is really is/was MBR or gpt.
Changing it can create lots of issue, but both Windows & Ubuntu will read partitions on either MBR or gpt partitioned drives.
So what was it?

Windows in MBR boot mode converts gpt drives to MBR incorrectly leaving backup gpt partition table. Then Linux tools see both and get confused, typically thinking you want to totally repartition & format (erase) drive. And if you have data you do not want that.

Post these:
sudo parted -l
sudo gdisk -l /dev/sdb

---

### Post by greenshirt11 on 2016-05-22
Hi,

Thanks for the quick answer. Output of commands below:


folkert@Atmananda:~$ sudo parted -l
Model: ATA Samsung SSD 840 (scsi)
Schijf /dev/sda: 250GB
Sectorgrootte (logisch/fysiek): 512B/512B
Partitietabel: gpt

Nummer  Begin   Einde   Grootte  Bestandssysteem  Naam                  Vlaggen
 1      1049kB  1050MB  1049MB   ntfs             Basic data partition  diag
 2      1051MB  1323MB  273MB    fat32            Basic data partition  opstart
 3      1323MB  164GB   163GB    ntfs             Basic data partition  msftdata
 4      164GB   176GB   12,3GB   linux-swap(v1)
 5      176GB   196GB   20,3GB   ext4
 6      196GB   197GB   512MB    ext4
 7      197GB   250GB   53,1GB   ext4


Waarschuwing: /dev/sdb bevat GPT-vingerafdrukken die aangeven dat het een 
GPT-tabel heeft.  Maar het bevat geen geldige nep-MSDOS-partitietabel, zoals zou
moeten.  Misschien werd deze beschadigd, mogelijk door een programma dat
GPT-partitietabellen niet begrijpt.  Of misschien hebt u de GPT-tabel verwijderd
en gebruikt nu een MSDOS-partitietabel.  Is dit echt een GPT-partitietabel?
Ja/Yes/Nee/No? Ja                                                         
Model: ATA ST500LT012-9WS14 (scsi)
Schijf /dev/sdb: 500GB
Sectorgrootte (logisch/fysiek): 512B/4096B
Partitietabel: gpt

Nummer  Begin   Einde   Grootte  Bestandssysteem  Naam                          Vlaggen
 1      1049kB  1050MB  1049MB   ntfs             Basic data partition          verborgen, diag
 2      1050MB  1322MB  273MB    fat32            EFI system partition          opstart, verborgen
 3      1322MB  2371MB  1049MB   fat32            Basic data partition          verborgen
 4      2371MB  2505MB  134MB                     Microsoft reserved partition  msftres
 5      2505MB  451GB   449GB    ntfs             Basic data partition          msftdata
 6      451GB   452GB   367MB    ntfs                                           verborgen, diag
 7      452GB   479GB   26,8GB   ntfs             Basic data partition          msftdata
 8      479GB   500GB   21,5GB   ntfs             Basic data partition          verborgen, diag


folkert@Atmananda:~$ sudo gdisk -l /dev/sdb
[sudo] password for folkert: 
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: present

Found valid MBR and GPT. Which do you want to use?
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer: 2
Using GPT and creating fresh protective MBR.
Disk /dev/sdb: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): DCD5D695-B459-4884-BF82-E287AC30A568
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2029 sectors (1014.5 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         2050047   1000.0 MiB  2700  Basic data partition
   2         2050048         2582527   260.0 MiB   EF00  EFI system partition
   3         2582528         4630527   1000.0 MiB  FFFF  Basic data partition
   4         4630528         4892671   128.0 MiB   0C01  Microsoft reserved part
   5         4892672       881684479   418.1 GiB   0700  Basic data partition
   6       881684480       882401279   350.0 MiB   2700  
   7       882401280       934830079   25.0 GiB    0700  Basic data partition
   8       934830080       976773119   20.0 GiB    2700  Basic data partition
folkert@Atmananda:~$

---

### Post by oldfred on 2016-05-22
It looks like gpt. 

Did you at one time create a hybrid MBR/gpt. The gpt protective MBR normally only has one entry for entire drive as gpt. That is so old tools that only work with MBR see drive as partitioned. Otherwise they may see it as blank and you partition it.

You can use the gdisk to correct MBR issues with a w command in its editing mode.
       GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by greenshirt11 on 2016-05-23
Thanks again. Will do some reading I guess.
Somewhere in my paper stuff there is an overview of the partitions when I created them; will need to find them first. 

It was a protective MBR because the GPT based laptop came with W8 installed on HDD.
An ubuntu version was installed on the HDD to create a dual-boot system.
Later I bought a SSD and copied the necessary data from the HDD to the SSD. 
The boot menu contained entries for booting from SSD or HDD (both W8 and Ubuntu).

From your response I guess that working with gdisk would be enough to get to system with recovered HDD so I can access my data again, right?

F

---

### Post by oldfred on 2016-05-23
If just partitioning issues gdisk would be the tool to use.

       repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

