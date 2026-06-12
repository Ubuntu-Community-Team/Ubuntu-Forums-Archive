---
title: "Cannot copy files from CD."
date: 2007-01-11
forum: General Help
---

### Post by true_friend on 2007-01-11
I have a problem i can not copy files from my cd rom. when i insert cd it mounts it in a new windows but when i try to copy any file it says cannot read ..(cds are checked on windows xp system they were ok)
my fstab is as follows
...................................
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1     /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda8       /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda9       /media/hda7     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom   udf,iso9660 user,noauto     0       0
.............................................
is there any deficiency here?
i think it is some permissions problem but root accounts also cannot do so i could not copy files through a root account.
plz help me.
Regards
True_Friend

---

### Post by hal10000 on 2007-01-11
insert a cd and in a terminal window do [COLOR="Red"]ls -l /media/cdrom [/COLOR]or [COLOR="Red"]ls -l /media/cdrom0[/COLOR] (depends on where you put the cd in).

Can you see the files on your cdrom?
Can you copy files from another cd (e.g.your ubuntu live cd)?

---

### Post by true_friend on 2007-01-11
this is the output of this command in terminal i inserted a kubuntu 6.06 live/install cd
..................................................
total 646
-r-xr-xr-x  1 root root     43 2006-05-28 21:43 autorun.inf
dr-xr-xr-x 10 root root   6144 2006-05-28 21:43 bin
dr-xr-xr-x  2 root root   2048 2006-05-31 08:33 casper
dr-xr-xr-x  5 root root   2048 2006-05-28 21:43 disctree
dr-xr-xr-x  3 root root   2048 2006-05-31 08:32 dists
dr-xr-xr-x  2 root root   2048 2006-05-31 08:33 install
dr-xr-xr-x  2 root root  10240 2006-05-31 08:33 isolinux
-r-xr-xr-x  1 root root 193110 2006-05-28 21:44 kubuntu.ico
-r--r--r--  1 root root  29100 2006-05-31 08:34 md5sum.txt
dr-xr-xr-x  2 root root   2048 2006-05-31 08:32 pics
dr-xr-xr-x  4 root root   2048 2006-05-31 08:32 pool
dr-xr-xr-x  2 root root   2048 2006-05-31 08:32 preseed
dr-xr-xr-x  8 root root   2048 2006-05-28 21:43 programs
-r--r--r--  1 root root    223 2006-05-31 08:32 README.diskdefines
-r-xr-xr-x  1 root root 364986 2006-05-01 22:00 start.bmp
-r-xr-xr-x  1 root root  38912 2003-11-18 00:09 start.exe
-r-xr-xr-x  1 root root     95 2005-06-29 15:23 start.ini
lr-xr-xr-x  1 root root      1 2006-05-31 08:32 ubuntu -> .
......................................................................
it copies some files but some files cannot be copied. i am wondering what is the problem.

---

### Post by hal10000 on 2007-01-11
Does this appear on both of your cd/dvd devices?
btw, I'm wondering too.

---

### Post by taurus on 2007-01-11
What are the files that won't let you copy to your harddrive?

---

### Post by true_friend on 2007-01-11
dat files.

---

### Post by taurus on 2007-01-11
> **true_friend said:**
> dat files.

Which dat files because I don't see any file starts with dat!

---

### Post by true_friend on 2007-01-11
*.dat
i mean movies files.

---

### Post by taurus on 2007-01-11
> **true_friend said:**
> *.dat
i mean movies files.

I don't see any *.dat on the CD!!!  :confused: 

```

total 646
-r-xr-xr-x 1 root root 43 2006-05-28 21:43 autorun.inf
dr-xr-xr-x 10 root root 6144 2006-05-28 21:43 bin
dr-xr-xr-x 2 root root 2048 2006-05-31 08:33 casper
dr-xr-xr-x 5 root root 2048 2006-05-28 21:43 disctree
dr-xr-xr-x 3 root root 2048 2006-05-31 08:32 dists
dr-xr-xr-x 2 root root 2048 2006-05-31 08:33 install
dr-xr-xr-x 2 root root 10240 2006-05-31 08:33 isolinux
-r-xr-xr-x 1 root root 193110 2006-05-28 21:44 kubuntu.ico
-r--r--r-- 1 root root 29100 2006-05-31 08:34 md5sum.txt
dr-xr-xr-x 2 root root 2048 2006-05-31 08:32 pics
dr-xr-xr-x 4 root root 2048 2006-05-31 08:32 pool
dr-xr-xr-x 2 root root 2048 2006-05-31 08:32 preseed
dr-xr-xr-x 8 root root 2048 2006-05-28 21:43 programs
-r--r--r-- 1 root root 223 2006-05-31 08:32 README.diskdefines
-r-xr-xr-x 1 root root 364986 2006-05-01 22:00 start.bmp
-r-xr-xr-x 1 root root 38912 2003-11-18 00:09 start.exe
-r-xr-xr-x 1 root root 95 2005-06-29 15:23 start.ini
lr-xr-xr-x 1 root root 1 2006-05-31 08:32 ubuntu -> .

```

---

### Post by true_friend on 2007-01-17
it was not in this cd
some other cd that was

---

