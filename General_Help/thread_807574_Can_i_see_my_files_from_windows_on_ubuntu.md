---
title: "Can i see my files from windows on ubuntu?"
date: 2008-05-25
forum: General Help
---

### Post by wijotoma on 2008-05-25
Hi, can someone tell me how to see my files from windows on ubuntu. I installed ubuntu in 40 Gb and the other 40 Gb i have windows, can i see the files i have at the windows vista partition on the ubuntu partition?

---

### Post by tamoneya on 2008-05-25
yes you can.  Please post the result of ```
sudo fdisk -l
```Then I can tell you the command for mounting your windows partition so you can read and write to it.

---

### Post by malachi1990 on 2008-05-25
Yeh, you should be able to simply go to places, computer, and you should see several volume mounts (your hard drives) and "filesystem."  Filesystem is your linux partition.  You should see a 40 gB hard drive along with whatever other drives you have.  If you don't, do what tamoneya said.

On mine, for example, I'll see a 131.6 GB media, and then all the files of the C drive.  And you should be done.

---

### Post by wijotoma on 2008-05-26
i tried what you two said, but still i can see them, what i can see now is my HP_recovery but the windows partition don't

---

### Post by vdawg on 2008-05-26
Please show us the output of fdisk -l

> **tamoneya said:**
> yes you can.  Please post the result of ```
sudo fdisk -l
```Then I can tell you the command for mounting your windows partition so you can read and write to it.

---

### Post by wijotoma on 2008-05-26
wilmerjose@wilmerjose-laptop:~$ sudo fdisk -l

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x95589558

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       18402   147814033+   7  HPFS/NTFS
/dev/sda2           18403       19457     8474287+   7  HPFS/NTFS

---

### Post by |Eric| on 2008-05-26
do a fdisk -l in a terminal window (application-> accessories  or run xterm by doing alt+F2) 
it will list partition that you have (drives if you will )
basicaly if you only have 2 partition : 


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         295     2369587   83  Linux  
/dev/sdc2             296        9729    75778605    c  W95 FAT32 (LBA)



where  /dev/sdc1 is your linux & /dev/sdc2 is your Windows (it could also be a NTFS partition)


if you have a HP_Backup or somthing like that i verry doubt that it contains your windows but try the folowing in a terminal window 
(type only whats after the #)

promt#   mount /dev/sdXX /mnt

where sdXX is the partition (drive) you whant to load


you can then access that drive in filesystem => mnt

please post the result here if you get any errors (even fdisk -l as this will help us understand the situation better)



EDIT : oh crap u running from CD ?


to access your drives 
open a terminal window  & paste the folloing :

 mkdir /mnt/sda1
 mkdir /mnt/sda2 
 mount /dev/sda1 /mnt/sda1
 mount /dev/sda2 /mnt/sda2


you should be able to access your files in filesystem/mnt/sda1 & sda2
also note that they may be read-only as the write driver is most likely not loaded

---

### Post by wijotoma on 2008-05-26
no, i'm not running from cd. 

I will prove that way and tell you if it worked

---

### Post by wijotoma on 2008-05-26
wilmerjose@wilmerjose-laptop:~$ mount/dev/sdXX/mnt
bash: mount/dev/sdXX/mnt: No existe el fichero ó directorio

---

### Post by |Eric| on 2008-05-26
if you have 2 drives as such :


Filesystem
HP_recovery 

there is 2 scenario that can give this result
A) you installed linux & formated : your windows files are gone! 
B) you installed linux & didnt format (verry possible since your partition is  still NTFS) : your files are interwined with linux files

how can you find out witch case we have here

open a filemanager (basicaly open your home dir & go up 2 notches (dblclick ".."  twice) 

you should be in either / or Filesystem (same) if you didnt format you will see a "window" & a "program files" folders (thats your windows)

if not its option A

Edit: you need spaces in the mount command ... mount (space) /dev/sda1 (space) /mnt/sda1 & for the mkdir : mkdir (space) /mnt/sda1

Edit2: in a terminal :  ls / 
& also a df


prompt# ls (space)/
promtt# df 


post it here

---

### Post by tamoneya on 2008-05-26
> **wijotoma said:**
> wilmerjose@wilmerjose-laptop:~$ mount/dev/sdXX/mnt
bash: mount/dev/sdXX/mnt: No existe el fichero ó directorio

that was a generic command.  He meant for you to modify it to your needs.  Here is the explict command to type:```
sudo mkdir /windows
sudo mount -t ntfs /dev/sda1 /windows
```Now browse to /windows and you will see your files.

---

### Post by wijotoma on 2008-05-26
i don believe is option A, because when i boot my pc i can star either windows or ubuntu, sometimes i use windows, sometimes ubuntu and my windows files are untouched

---

### Post by tamoneya on 2008-05-26
> **|Eric| said:**
> if you have 2 drives as such :


Filesystem
HP_recovery 

there is 2 scenario that can give this result
A) you installed linux & formated : your windows files are gone! 
B) you installed linux & didnt format (verry possible since your partition is  still NTFS) : your files are interwined with linux files

how can you find out witch case we have here

open a filemanager (basicaly open your home dir & go up 2 notches (dblclick ".."  twice) 

you should be in either / or Filesystem (same) if you didnt format you will see a "window" & a "program files" folders (thats your windows)

if not its option A

Edit: you need spaces in the mount command ... mount (space) /dev/sda1 (space) /mnt/sda1 & for the mkdir : mkdir (space) /mnt/sda1

Edit2: in a terminal :  ls / 
& also a df


prompt# ls (space)/
promtt# df 


post it here

From looking at fdisk output it looks like windows is perfectly fine.  You can see both the main windows partition (sda1) and the smaller recovery partition (sda2).  The thing that looks most odd to me is that there is no linux partition.

---

### Post by wijotoma on 2008-05-26
wilmerjose@wilmerjose-laptop:~$ sudo mkdir /windows
[sudo] password for wilmerjose: 
Sorry, try again.

i can't insert that command, and when i type my password it says it is wrong

---

### Post by strabes on 2008-05-26
> **wijotoma said:**
> wilmerjose@wilmerjose-laptop:~$ sudo mkdir /windows
[sudo] password for wilmerjose: 
Sorry, try again.

i can't insert that command, and when i type my password it says it is wrong

That means you're typing it wrong. Do you have capslock on?

---

### Post by wijotoma on 2008-05-26
no, i am sure i'm typing the correct one

this pass is the same with the one you log in at the start?

---

### Post by wijotoma on 2008-05-26
wilmerjose@wilmerjose-laptop:~$ sudo mkdir /windows
[sudo] password for wilmerjose: 
mkdir: no se puede crear el directorio `/windows': El fichero ya existe
wilmerjose@wilmerjose-laptop:~$ sudo mount -t ntfs /dev/sda1 /windows
wilmerjose@wilmerjose-laptop:~$

---

### Post by wijotoma on 2008-05-26
hey guys, now checking up filesystem i found windows folders at "host", but i see the folders but not the files

---

