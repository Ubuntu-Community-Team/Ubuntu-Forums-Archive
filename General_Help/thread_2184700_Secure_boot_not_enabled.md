---
title: "Secure boot not enabled"
date: 2013-10-30
forum: General Help
---

### Post by makkekkazzo on 2013-10-30
Hi to everybody,
I'm new to the forum and to Ubuntu LST 12.04 (I have returned to Ubuntu after a pair of years). I've installed 12.04, as a single boot, on a pre-installed WIN8 ASUS F55A with UEFI and Secure Boot activated. For installing Ubuntu I've followed the guide to disable Secure Boot and everything went good. The only problem is that now for less than a second before the GRUB menu appears a black screen with this four lines:

Secure boot not enabled
error: efidisk read error.
error: efidisk read error.
error: efidisk read error.

Is this a problem, or could this create a problem in the future, to the performance of my laptop? It is possible to eliminate?

Thanks a lot to everybody
And Have a happy day

---

### Post by fantab on 2013-10-30
Post the output of:
```
sudo fdisk -l
sudo parted -l
```

---

### Post by makkekkazzo on 2013-10-30
This one is the first
```
makkekkazzo@fra:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 testine, 63 settori/tracce, 60801 cilindri, totale 976773168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Identificativo disco: 0x04a53d1b

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.
```

And this is the second:
```
makkekkazzo@fra:~$ sudo parted -l
Modello: ATA Hitachi HTS54505 (scsi)
Disco /dev/sda: 500GB
Dimensione del settore (logica/fisica): 512B/4096B
Tabella delle partizioni: gpt

Numero  Inizio  Fine   Dimensione  File system     Nome                  Flag
 1      1049kB  316MB  315MB       fat32           EFI system partition  avvio
 2      316MB   201GB  201GB       ext4
 3      201GB   496GB  294GB       fat32
 4      496GB   500GB  4182MB      linux-swap(v1)
```

Thanks a lot for the fast reply.

---

### Post by oldfred on 2013-10-30
It may just be old UEFI entries. 
That UEFI says secure boot not enabled is just a message.
And UEFI remembers entries in its firmware. You may have old Windows entries and then those give an error if it cannot read them in efi partition.

Some UEFI show you the info, others do not and you have to use the command line efibootmgr.

 # from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

### Post by fantab on 2013-10-31
Your first partition should start at 1048 and not 1049. This is why your output says "Partition 1 does not start on physical sector boundary". You can fix this with Gparted, For more details see [http://askubuntu.com/questions/156994/partition-does-not-start-on-physical-sector-boundary](http://askubuntu.com/questions/156994/partition-does-not-start-on-physical-sector-boundary)

Like oldfred points out "error: efidisk read error" could be because of the old Windows boot entry trying to read from either the Linux Partition or 'mis-aligned' first EFI partition.

---

### Post by makkekkazzo on 2013-10-31
Hi,
thanks a lot for the help, I've succesfully deleted the windows partition with: 
```
sudo efibootmgr -v 
sudo efibootmgr -b0000 -B
```
and then I've followed the suggestion to move the partition (sorry "fantab" but I didn't understood how to pass from 1049 to 1048, so I tried the link suggestion and give to the partition a 1MB free before that with gparted).

But both the things still stays in their place: the lines at boot still are there and this are the new sudo fdisk -l and sudo parted -l
```
makkekkazzo@fra:~$ sudo fdisk -l
[sudo] password for makkekkazzo: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
  

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 testine, 63 settori/tracce, 60801 cilindri, totale 976773168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Identificativo disco: 0x04a53d1b

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.
makkekkazzo@fra:~$ sudo parted -l
Modello: ATA Hitachi HTS54505 (scsi)
Disco /dev/sda: 500GB
Dimensione del settore (logica/fisica): 512B/4096B
Tabella delle partizioni: gpt

Numero  Inizio  Fine   Dimensione  File system     Nome                  Flag
 1      2097kB  317MB  315MB       fat32           EFI system partition  avvio
 2      317MB   201GB  201GB       ext4
 3      201GB   496GB  294GB       fat32
 4      496GB   500GB  4182MB      linux-swap(v1)


```

Again thank for the replies

---

### Post by oldfred on 2013-10-31
I think your start is ok. 
fdisk does not work on gpt drives, but suposedly they have a new version in development.

sudo parted -l shows size not start. from my SSD which is gpt partitioned.

```
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sdd: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  316MB   315MB   fat32                 boot
 2      316MB   317MB   1049kB                        bios_grub
 3      317MB   30.2GB  29.9GB  ext4         Precise
 4      30.2GB  60.0GB  29.9GB  ext4         Quantal
```


You do want first sector to be 2048
```
fred@fred-Precise:~$ sudo parted /dev/sdd unit s print
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sdd: 117231408s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End         Size       File system  Name     Flags
 1      2048s      616447s     614400s    fat32                 boot
 2      616448s    618495s     2048s                            bios_grub
 3      618496s    58925055s   58306560s  ext4         Precise
 4      58925056s  117229743s  58304688s  ext4         Quantal

```

---

### Post by makkekkazzo on 2013-10-31
Thank you very much guys, sorry for having you wated your time, no everything is in the right location (ie 2048s).

---

### Post by makkekkazzo on 2013-11-05
Sorry but after the first boot without the problem, it has returned as before.
Here are the results of the commands
```

sudo parted -l
sudo parted /dev/sda unit s print
sudo fdisk -l

```

```
makkekkazzo@fra:~$ sudo parted -l
Modello: ATA Hitachi HTS54505 (scsi)
Disco /dev/sda: 500GB
Dimensione del settore (logica/fisica): 512B/4096B
Tabella delle partizioni: gpt

Numero  Inizio  Fine   Dimensione  File system     Nome                  Flag
 1      1049kB  317MB  316MB       fat32           EFI system partition  avvio
 2      317MB   201GB  201GB       ext4
 3      201GB   496GB  294GB       fat32
 4      496GB   500GB  4182MB      linux-swap(v1)


makkekkazzo@fra:~$ sudo parted /dev/sda unit s print
Modello: ATA Hitachi HTS54505 (scsi)
Disco /dev/sda: 976773168s
Dimensione del settore (logica/fisica): 512B/4096B
Tabella delle partizioni: gpt

Numero  Inizio      Fine        Dimensione  File system     Nome                  Flag
 1      2048s       618495s     616448s     fat32           EFI system partition  avvio
 2      618496s     393433087s  392814592s  ext4
 3      393433088s  968605695s  575172608s  fat32
 4      968605696s  976773119s  8167424s    linux-swap(v1)

makkekkazzo@fra:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 testine, 63 settori/tracce, 60801 cilindri, totale 976773168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Identificativo disco: 0x04a53d1b

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.
```

---

### Post by oldfred on 2013-11-05
Just to see if anything looks wrong post a link to the report.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by makkekkazzo on 2013-11-10
OK thanks.
The link is [http://paste.ubuntu.com/6394919/](http://paste.ubuntu.com/6394919/)
And other odd thing is that every time I'm booting from liveCD the booting options are replicanting, in the beginning were only 2, now are like in the picture.[ATTACH=CONFIG]247722[/ATTACH]

Thanks again

---

### Post by oldfred on 2013-11-10
Some messages are extranous. See post #11.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1097570](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1097570)

Boot-Repair usually runs this. Your UEFI remembers settings in its NVRAM.

       sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

And then you may be able to remove extra or duplicate entries.

---

### Post by makkekkazzo on 2013-11-10
I've already done the things with efibootmgr, do I have to do it again?

---

### Post by oldfred on 2013-11-10
If somehow it is adding entries you may have to keep deleteing them? 

Real solution is to find out what is adding them? But I have no idea.

---

