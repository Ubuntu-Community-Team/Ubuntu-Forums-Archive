---
title: "gmailfs working?"
date: 2005-04-08
forum: General Help
---

### Post by brickbat on 2005-04-08
hi,  i think i have followed the instructions properly and i get no errors.but

i dont think its working because when i log into the gmail account, no memory is used up even though i have copied lots of data to the directory.

here is my setup

in fstab:
/usr/local/bin/gmailfs.py /media/gdisk1 gmailfs noauto,username=backdisk1,password=mybusiness,fsname=metoo2

in /media/ i created an /gdisk1 directory and set the appropriate write permissions.

am i missing something?

ciao
bb

---

### Post by lao_V on 2005-04-08
what do u get when you do 'ls' or df in your gmailfs mount?

---

### Post by brickbat on 2005-04-08
when i copy some files to it and list them they are there.

here is what df shows

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hdb6              9629880   4310248   4830456  48% /
tmpfs                   323276         0    323276   0% /dev/shm
/dev/hdb11            16429268   4010672  11584024  26% /media/lindata
/dev/hdb9             33317944  33047684    270260 100% /media/music
/dev/hda1              8104976   8079016     25960 100% /media/boot
/dev/hdb8              8257292   7883944    373348  96% /media/data
/dev/hdb10            16683468   6051396  10632072  37% /media/scratch
/dev/hdb5             14860832  13664464   1196368  92% /media/dloads
/dev/hda5             11804224  11599960    204264  99% /media/library
/dev/hdb1             20472816  19006208   1466608  93% /media/winxp
/dev                   9629880   4310248   4830456  48% /.dev
none                      5120      2908      2212  57% /dev

hdb6 is my linux partition.

---

### Post by lao_V on 2005-04-08
That would suggest that its working :-) Maybe gmail isn't able to update files stored this way?

---

### Post by brickbat on 2005-04-08
but shouldnt it be giving me the free space off gmail?

also there is nothing there when i log into gmail. gmail tells me i have use 0mb even though i copies 20mg to the drive,

---

### Post by confused_user on 2005-09-30
can i ask a question?, how the hell did you get it working in the first place?

So many threads here are sayign that it just doesnt work.

I would love to know hoe you did it so i can try

many thanks

---

