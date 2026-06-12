---
title: "conky script issue"
date: 2015-09-08
forum: General Help
---

### Post by alain.roger on 2015-09-08
Hi,

i have conky installed and multi script are launched at boot.
everything is ok except that i have a NAS and I monitor 2 shared folder of the NAS using conky.
my NAS is 4 TB huge and i would like to know their respective size.

e.g. /perso and /work have different size GB used) however my conky script return the same size for both.
       [FONT=monospace][COLOR=#000000]${color #ffc000}/storage ${color #888888}$alignr${fs_used /media/work} [/COLOR]
${color white}${fs_bar 6 /media/work} 
${color #ffc000}/perso ${color #888888}$alignr${fs_used /media/perso} 
${color white}${fs_bar 6 /media/perso}

both /media/work and /media/perso are mounted at the boot session automatically.

So why is my mistake ?

thx
[/FONT]

---

### Post by deadflowr on 2015-09-19
Are the two directories part of the same partition?
(In fstab do they share the same UUID, or <file system> option)

---

### Post by alain.roger on 2015-09-20
In fstab they do not share the same UUID as there is no UUID for network directories shared.

> [COLOR=#000000]//n4200eco/Work /media/work cifs auto,iocharset=utf8,credentials=/home/alain/.smbcredentials,uid=1000,gid=users,file_mode=0775,dir_mode=0775 0 0 [/COLOR]
[FONT=monospace]//n4200eco/Perso /media/perso cifs auto,iocharset=utf8,credentials=/home/alain/.smbcredentials,uid=1000,gid=users,file_mode=0775,dir_mode=0775 0 0


but as they are directories of the same NAS (4 HDD of 4 TB) in raid10, i believe that they have the same hidden UUID (//n4200eco)

filesystem is by documentation, different //n4200eco/Perso and //n4200eco/Work

so i do not know what to do.
if i run a du -sh on som subdirectories of any of those 2 mounted points, i got the correct info but it takes sometimes 10 minutes to get info back to terminal and it can not be like that in conky.

[/FONT]

---

### Post by alain.roger on 2016-06-15
i tried du -sh /mnt/perso and it returned 255TB while my NAS is no more than 12 TB and in fact using raid6 it it a 5.5TB.
According to Double COmmander, the /mnt/perso uses 850 GB which is basically the correct figure.

So why du -sh returns 255TB ? How to do in conky to get the correct number, so the number as double commander returns (850GB) ?

thx

---

### Post by Habitual on 2016-06-15
Not sure you can "make conky" do this. If the code/math isn't there, the code/math isn't there
You may have to wrap your du in a shell script and execpi the script.sh

---

### Post by alain.roger on 2016-06-15
In fact i discovered that if there are files with a zero size "du" returns crazy values. It needs to be confirmed but directories with no zero-size file is ok, while directory with at least 1 zero-size file returns a crazy value

---

### Post by alain.roger on 2016-06-18
So i was successful to get the correct valu doing as following:
1. sudo chmod u+s /usr/bin/du
2. now i can do : du -hs /mnt/perso and get the correct value

---

