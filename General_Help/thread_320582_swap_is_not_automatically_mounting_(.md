---
title: "swap is not automatically mounting :("
date: 2006-12-17
forum: General Help
---

### Post by Maelgwyn on 2006-12-17
Hey guys,

I've been having trouble with my comp running really slowly, and a mate suggested I run ```
$ top
```, which I did and it turns out I have no swap!

So I fired up Gparted, and clicked swapon, but since I've rebooted, it hasn't stayed 'on'... How do I fix this please?

---

### Post by meng on 2006-12-17
Post the result of:
fdisk -l

and of:
cat /etc/fstab

EDIT:
make that
sudo fdisk -l

---

### Post by Hossie on 2006-12-17
```
sudo echo "/dev/sda1 none swap sw 0 0" >> /etc/fstab
```

Of course, change the "sda1" to your actual swap partition.

---

### Post by Maelgwyn on 2006-12-19
sudo fdisk -l gives me```
Disk /dev/hda: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         637     5116671   83  Linux
/dev/hda2             638         701      514080   82  Linux swap / Solaris
/dev/hda3             702        1911     9719325   83  Linux
/dev/hda4            1912        2480     4570492+  83  Linux

```

cat /etc/fstab gives
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=35a2478a-9664-45f1-af9b-8013b8ecf790 /               reiserfs notail          0       1
# /dev/hda3
UUID=ae152a58-c26f-4dae-92b3-66951b9ef327 /home           ext3    defaults        0       2
# /dev/hda2
UUID=0bdc4c60-ba27-4e4d-b7d4-e610de789a58 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

and Hossie, your command gives me 
```
bash: /etc/fstab: Permission denied
```

---

### Post by taurus on 2006-12-19
Edit your /etc/fstab

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and remove this line
```
UUID=0bdc4c60-ba27-4e4d-b7d4-e610de789a58 none         swap    sw       0       0
```
and replace that with
```
/dev/hda2   none   swap   sw   0   0
```
and reboot...

Then, see if the swap partition is mount with

```
free
```

---

### Post by anaconda on 2006-12-19
are you sure your swap partition is actually made to be swap?

sudo mkswap /dev/hda2
sudo swapon /dev/hda2

And do as "taurus" said and change the UUID addres to be old fashion 
/dev/hda2 none  swap sw 0 0
because if I remember correctly UUID can change when reformatting or running mkswap.. not 100% sure if UUID can change though..

---

### Post by bodhi.zazen on 2006-12-19
> **anaconda said:**
> are you sure your swap partition is actually made to be swap?

sudo mkswap /dev/hda2
sudo swapon /dev/hda2

And do as "taurus" said and change the UUID addres to be old fashion 
/dev/hda2 none  swap sw 0 0
because if I remember correctly UUID can change when reformatting or running mkswap.. not 100% sure if UUID can change though..

UUID will change whenever you format the partition.

To list your devices by uuid:```
ls /dev/disk/by-uuid -lh
```

You can use either UUID={greek} or /dev/hdxy in fstab.

Update fstab either your new swap UUID or /dev/hda2 as instructed by taurus :p

[http://en.wikipedia.org/wiki/UUID](http://en.wikipedia.org/wiki/UUID)

---

### Post by Maelgwyn on 2006-12-20
ok, so I followed Taurus' advice and here's what happened after the reboot:
```
cerddorion@BigCalm:~$ free
             total       used       free     shared    buffers     cached
Mem:        254960     250948       4012          0      11628     108460
-/+ buffers/cache:     130860     124100
Swap:            0          0          0
cerddorion@BigCalm:~$ 
cerddorion@BigCalm:~$ sudo mkswap /dev/hda2
Password:
Setting up swapspace version 1, size = 526413 kB
no label, UUID=bc427eee-8453-4d2c-b28a-e4c2ea115f27
cerddorion@BigCalm:~$ sudo swapon /dev/hda2
cerddorion@BigCalm:~$ free
             total       used       free     shared    buffers     cached
Mem:        254960     249372       5588          0        936      57204
-/+ buffers/cache:     191232      63728
Swap:       514072          0     514072
cerddorion@BigCalm:~$ 
```

---

### Post by Maelgwyn on 2006-12-23
Fixed :D

---

### Post by Azakus on 2006-12-23
> **anaconda said:**
> are you sure your swap partition is actually made to be swap?

sudo mkswap /dev/hda2
sudo swapon /dev/hda2

And do as "taurus" said and change the UUID addres to be old fashion 
/dev/hda2 none  swap sw 0 0
because if I remember correctly UUID can change when reformatting or running mkswap.. not 100% sure if UUID can change though..

UUID changes if you remake the swap, every time.

---

