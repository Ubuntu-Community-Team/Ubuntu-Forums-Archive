---
title: "GParted unused size 80 Gio vs Thunar 6.5 Go"
date: 2017-01-17
forum: General Help
---

### Post by spade on 2017-01-17
Hello Everybody,

I have the feeling my recurrent problem is basic and explanations have been given a long time ago, but I can't find them.
I have a big 1.8 Tio ext4 partition.
GParted reports ~80 Gio of unused space.
Thunar reports 6.5 Go of free space.
Unfortunatally, the Thunar number look to be true when I fill the partition of 6.5 Go data with a third software that reports the partition is full.
The problem is not vital when the partition is not almost full, but why GParted is so far from reality ?
The difference of Go and Gio does not explain a so big difference.

Thanks.

---

### Post by &amp;KyT$0P# on 2017-01-17
With this partition mounted, please post the output of these Terminal commands -
```
df -hT
df -ihT
```

---

### Post by oldfred on 2017-01-17
Approx 80 GB sounds like 5% of your drive.
 Also in Linux the default is to reserve 5% of the diskspace for the superuser (this can be adjusted using tune2fs -m). 

But that really only is required for / (root) and was back when drives where a lot smaller.

See -m option in:
man tune2fs 

Explains why and 5% is default. 

If just a data partition you may not need any reserved blocks. But still should monitor system regularly to make sure it does not get too full.

---

### Post by spade on 2017-01-18
```
$ df -hT /dev/sdg6
Sys. de fichiers Type Taille Utilisé Dispo Uti% Monté sur
/dev/sdg6        ext4   1,8T    1,7T  2,8G 100% /mnt/GrosFichiers
```
```
$ df -ihT /dev/sdg6
Sys. de fichiers Type Inœuds IUtil. ILibre IUti% Monté sur
/dev/sdg6        ext4   230M    29K   230M    1% /mnt/GrosFichiers
```

The first command looks correct (I have filled it more since my first post)
I'm going to try the tunefs command.

---

### Post by spade on 2017-01-18
OK I unmounted sdg6 then run the following command :
```
$ sudo tune2fs -m 1 /dev/sdg6
```
then remounted sdg6 then run:
```
$ df -hT /dev/sdg6
Sys. de fichiers Type Taille Utilisé Dispo Uti% Monté sur
/dev/sdg6        ext4   1,8T    1,7T   58G  97% /mnt/GrosFichiers
```
GParted now gives 76 Gio unused
which is consistent with 58Gio + 1800/100 = 76 Gio

So my question is: why GParted does not give the "real" free (available) space ?
"unused" is a bit confusing, because a part of it is used by the system.

---

### Post by oldfred on 2017-01-18
How ever you calculate it, you drive is full. Best to always have some space.
Windows NTFS wants 30% free to work well at 10% with NTFS you just about cannot do defrag. 

With Linux you do not need quite as much free space but need some.

Formatting a partition uses space for the journal and internal structures.
Some tools just include unformatted, formatted, or include the hidden reserved space.

---

