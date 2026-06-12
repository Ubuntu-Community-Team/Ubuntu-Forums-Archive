---
title: "error when trying to create a bootable img from clonezilla backup"
date: 2018-11-14
forum: General Help
---

### Post by rosika on 2018-11-14
Hello,


I´ve run into a problem when trying to create a mountable img out of a *clonezilla-backup*.


For doing this I used
```
sudo cat /dir-to-images/sdb1.ext4-ptcl-img.gz.* | sudo gzip -d -c | sudo partclone.ext4 -C -r -W -s - -O /dir-to-new-image/hda1.img



```which in my case translates to


```
sudo cat /media/rosika/58B6A7DE7CA15FC5/Lubuntu_2018-10-16-09-img/sdd2.ext2-ptcl-img.gz.* | sudo gzip -d -c | sudo partclone.ext2 -C -r -W -s - -O /media/rosika/545A-B3AE/sdd2.img



```This worked for a few minutes:


```
Partclone v0.2.86 http://partclone.org
Starting to restore image (-) to device (/media/rosika/545A-B3AE/sdd2.img)
Calculating bitmap... Please wait... done!
File system:  EXTFS
Device size:   38,2 GB = 9329920 Blocks
Space in use:  27,3 GB = 6663415 Blocks
Free Space:    10,9 GB = 2666505 Blocks
Block size:   4096 Byte

```

 but after 12,33% completion it stopped and I got the error-message:


```
target seek ERROR:Das Argument ist ungültigpleted:  12,33%, 848,55MB/min,       
Partclone fail, please check /var/log/partclone.log !2,37%, 843,94MB/min,   

```

I looked up the log-entries:


```
Partclone v0.2.86 http://partclone.org
Starting to restore image (-) to device (/media/rosika/545A-B3AE/sdd2.img)
we need memory: 1174500 bytes
image head 4160, bitmap 1166240, crc 4100 bytes
Calculating bitmap... Please wait... done!
File system:  EXTFS
Device size:   38,2 GB = 9329920 Blocks
Space in use:  27,3 GB = 6663415 Blocks
Free Space:    10,9 GB = 2666505 Blocks
Block size:   4096 Byte
target seek ERROR:Das Argument ist ungültig   # invalid argument



```I´m really at loss here. Can anybody help me?


Tnx a lot in advance.


Rosika  :confused:

P.S:
system: Lubuntu 16.04.5 LTS, 64 bit
partclone: 0.2.86-1

---

### Post by rosika on 2018-11-15
[FONT=Arial][I][B]UPDATE

[/B][/I][/FONT]
[FONT=Arial]Hi again.

[/FONT]
[FONT=Arial]In the meanwhile I could solve my problem (with the help of user dc.901 from linuxquestions, see: [https://www.linuxquestions.org/questions/linux-software-2/error-when-trying-to-create-a-bootable-img-from-clonezilla-backup-4175642336/](https://www.linuxquestions.org/questions/linux-software-2/error-when-trying-to-create-a-bootable-img-from-clonezilla-backup-4175642336/) )

[/FONT]
[FONT=Arial]For anybody interested here´s the solution:

[/FONT]
[FONT=Arial]This time I chose the third partition of my HDD for my output file where there was enough free space for sure.[/FONT]
[FONT=Arial]My new command was

[/FONT]
```
[FONT=Arial]sudo cat /media/rosika/58B6A7DE7CA15FC5/Lubuntu_2018-10-16-09-img/sdd2.ext2-ptcl-img.gz.* | sudo gzip -d -c | sudo partclone.ext2 -C -r -W -s - -O /media/rosika/f14a27c2-0b49-4607-94ea-2e56bbf76fe1/kgw/Neu/sdd2.img
[/FONT]
```[FONT=Arial]
And: this time the whole process went through to 100 %. Output: “cloned successfully”.

[/FONT]
[FONT=Arial]Being excited as far as the result is concerned I mounted the resulting sdd2.img with

[/FONT]
[FONT=Arial]```
sudo mount -o loop ./sdd2.img /mnt

```
from the respective directory.
Unmounting went well with[/FONT]
[FONT=Arial]```
sudo umount sdd2.img

```
And indeed: it granted me access to all my personal data from my /home-directory which I had created with clonezilla.

[/FONT]
[FONT=Arial]Of course I wanted to find out why things didn´t go well in the first place.

[/FONT]
[FONT=Arial]My original command referred to a 128 GB stick with two equally large partitions.

[/FONT]
[FONT=Arial]On the 1st one there is my clonezilla data. The second partition was empty. So I thought. But it turned out that in “trash” there were several 4 GB chunks of data. And indeed 33 % of the partition was used. I really didn´t know that.

[/FONT]
[FONT=Arial]That seems to have been the reason. Not enough disk space. [/FONT]
[FONT=Arial]So it seems everything works fine now.

[/FONT]
[FONT=Arial]Greetings
Rosika ;)[/FONT]

---

