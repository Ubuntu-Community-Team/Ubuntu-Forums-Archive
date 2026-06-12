---
title: "Recover damaged partition"
date: 2014-05-16
forum: General Help
---

### Post by Patricia_Budamis on 2014-05-16
Hello :)

I'd like to know how to recover some files in a damaged partition.

The situation is as following: I had windows 7 installed in a 1tb HD with just 1 partition, then I decided to install ubuntu 14.04 in the same hd. I used the ubuntu live cd partition manager to create a 80gb partition, I marked it as ext4 and put to format from the beggining of the 1tb partition, and I guess that was the problem, probably it overwrote some data from windows, because now I can access the ubuntu normally, but it cannot find my other partition (the windows one). In /dev I see that I have both sda e sda1, but I cannot mount it.

If I run "[FONT=arial]sudo gdisk -l /dev/sda" I get the following (it was translated by myself):[/FONT]


WARNING: GPT (Partition table GUID) detected in '/dev/sda'! The fdisk does not support GPT. Use GNU Parted.




Disc /dev/sda: 1000.2 GB, 1000204886016 bytes
255 cabeças, 63 setores/trilhas, 121601 cilindros, total of 1953525168 sectors
Unidades = setores de 1 * 512 = 512 bytes
Tamanho do setor (lógico/físico): 512 bytes / 4096 bytes
Tamanho da E/S (mínimo/ideal): 4096 bytes / 4096 bytes
Identificador do disco: 0x381a56bd


Dispositivo Boot      Begging        End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.


Disco /dev/sdb: 7933 MB, 7933526016 bytes
245 cabeças, 62 setores/trilhas, 1020 cilindros, total of 15495168 sectors
Unidades = setores de 1 * 512 = 512 bytes
Tamanho do setor (lógico/físico): 512 bytes / 512 bytes
Tamanho da E/S (mínimo/ideal): 512 bytes / 512 bytes
Disc identifier: 0x00000000


Dispositivo Boot      Begging        End      Blocks   Id  System
/dev/sdb1              62    15493799     7746869    b  FAT32 W95


I also tried "testdisk", and it lists 6 ntfs partitions, by none of them I can list the files because it says the partition is damaged. I have no idea of what I can do now.

Any help is really appreciated! Thanks in advance :)

---

### Post by kira_belka2 on 2014-05-16
hi.. you can use get "databack ntfs" utility or rstudio.. or testdisk (raw recovery).. but it seems that you really overwrote ntfs partition..
so not so much chances to return all data.
and right... you should use "parted" or "gparted" (I suppose you use gui :) ) just because your disks > 1TB.
so your output shows that  you have 2 physical disks :)
try
 sudo parted -l

---

### Post by stalkingwolf on 2014-05-17
there is a windows application that is called pandora that might do the trick.havent used it in years but it was still available a year and a half ago

---

### Post by Patricia_Budamis on 2014-05-17
Thank you both for the reply :D I already tried testdisk but it can't list the files in the partitions, it also lists many more partitions than I thought I had. And I don't have windows installed, just ubuntu, so I have to use something for linux.

In the end I was able to retrieve my data using dd and foremost, but I wish I could retrieve all the folder structure and file names :s

I saw that there is a program that maybe could do the trick "easeus" but it's just for windows. I was thinking in maybe retrieve all data that I can with foremost, then install windows in this 80gb partition just to try to recover the lost partition using this software, and then reformat the computer a third time :)

---

### Post by oldfred on 2014-05-17
Was your Windows 7 installed in UEFI mode? Most Windows 7 systems were installed in BIOS boot mode, but a few were UEFI.
Windows only boots from gpt partitioned drives with UEFI.
Both Windwos & Ubuntu only boot from MBR(msdos) partitioned drives with BIOS.

If you converted a gpt drive to BIOS by installing Windows 7 over a Windows 8 gpt drive it converted it incorrectly and left the backup gpt partition table. Then depending on what you did you may have converted it to gpt and Windows in BIOS mode will not work.

Post this:
       sudo parted /dev/sda unit s print

---

### Post by stalkingwolf on 2014-05-17
the first time i used pandora it recovered files three layers deep. i ended up with files from a previous owner.  there are several tools on hieren disk

---

