---
title: "Partition Help."
date: 2008-02-20
forum: General Help
---

### Post by AndreSantos on 2008-02-20
This is my df -h:
```

Sist. Arq.            Tam   Usad Disp  Uso% Montado em
/dev/sda1             5,1G  4,4G  656M  88% /
varrun                982M   84K  982M   1% /var/run
varlock               982M     0  982M   0% /var/lock
udev                  982M   60K  982M   1% /dev
devshm                982M     0  982M   0% /dev/shm
lrm                   982M   34M  948M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda3              50G   33M   50G   1% /media/sda3

```

I would like to know if there is a way to enlarge my root partition, without having to do a fresh install. I would copy the stuff on sda3 to sda1 and then format sda3. After that i would enlarge sda1 with the free space from sda3. is something like that possible?

---

### Post by bodhi.zazen on 2008-02-20
You can enlarge / from a live CD with Gparted. It is on the Desktop CD. You will need to user Ubuntu 7.10 or download PartedMagic.

[http://www.digitalincursion.net/partedmagic/pmagic-2.0.iso](http://www.digitalincursion.net/partedmagic/pmagic-2.0.iso)

---

### Post by AndreSantos on 2008-02-20
Im going to try gParted Live CD tomorrow.
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

Do u think it might work out?

---

### Post by bodhi.zazen on 2008-02-20
Should work just fine.

---

### Post by gimfred on 2008-02-20
The short answer is yes, however there are a few catches. You have to make sure all attributes are kept the same. Also you need to make sure that your /boot/ refers to the correct device. All in all very possible, and not as hard as I've made it sound. 

It may be easier though to back up the /home directory and move that to your sda3 partition. 

Here is my setup:

```
~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/hda5             2.3G  260M  2.0G  12% /
varrun               1008M  240K 1007M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M  128K 1008M   1% /dev
devshm               1008M     0 1008M   0% /dev/shm
lrm                  1008M   38M  970M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/hda1             114M   24M   85M  23% /boot
/dev/hdd1             115G   52G   63G  46% /home
/dev/hdb1              28G   24G  3.5G  88% /media/hdb1
/dev/hdb2             9.5G   71M  9.5G   1% /media/hdb2
/dev/hda9              14G  164M   13G   2% /opt
/dev/hda7             4.6G  138M  4.3G   4% /srv
/dev/hda6             1.9G   36M  1.8G   2% /tmp
/dev/hda10             14G  7.0G  6.1G  54% /usr
/dev/hda8             4.6G  1.2G  3.2G  28% /var

```

As you can see I have quite a few partitions! For simplicity yet portability 3 partitions are all that is needed. 
> / = root (you know this)
/home = partition for user data (your data -- probably what is filling up your / partition anyway).
swap = pretty self descriptive

Psychocats does a better explanation of the partitioning recommendations at : [http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning").

To [partition home]("http://www.psychocats.net/ubuntu/separatehome").

---

### Post by AndreSantos on 2008-02-21
I cant manage to boot from gparted live cd. Is it compatible with amd processors? I dont know what option i should select when its time to boot. Can you give me some help on that? After i select the option, it start to boot but then the screen freezes, and all the stuff that was being displayed gets messed up.

Also, thanks for the advice gimfred, im going to use that 3 partitions. 

Waiting for some help.

---

### Post by bodhi.zazen on 2008-02-21
Although the Gparted live CD is a useful tool, it is unnecessary. You can manage your partitions with any live CD, including the Ubuntu Desktop CD. Ubuntu 7.10 has gparted on it.

---

### Post by AndreSantos on 2008-02-21
But i dont got Ubunu 7.10 live CD here, thats why im trying with gparted's.

---

### Post by bodhi.zazen on 2008-02-21
Try the safe graphic mode (boot option)

If that fails you will need to try an alternate live CD. You could try Parted Magic

[http://www.digitalincursion.net/partedmagic/pmagic-2.0.iso](http://www.digitalincursion.net/partedmagic/pmagic-2.0.iso)

---

### Post by AndreSantos on 2008-02-21
Ok, worked with Parted Magic. Is there a safe way to move files from one partition to another? I want to move whats on sda3 to sda1, so i can resize sda1.

---

### Post by bodhi.zazen on 2008-02-21
Sure, manually mount 'em & copy the data.

Open a terminal

mkdir /mnt/sda3 /mnt/sda1
mount /dev/dsa3 /mnt/sda3
mount /dev/sda1 /mnt/sda1

Open a filemanager (Thunar ?) and copy away ;)

---

### Post by AndreSantos on 2008-02-22
After copying, do i have to delete /mnt/ ? Or do something to unmount ?

---

### Post by bodhi.zazen on 2008-02-22
> **AndreSantos said:**
> After copying, do i have to delete /mnt/ ? Or do something to unmount ?

**NO, DON'T DO THAT**

to unmount, use well umount (no n)

umount /mnt/sda1
umount /mnt/sda3

---

### Post by AndreSantos on 2008-02-22
Hello,

I like you told me to do, but im having one problem. I managed to enlarge sda1. On parted magic, i created sda3 again. Everything worked fine. But when i rebooted, it shows some errors with the filesystem. I gave the root pass, but nothing was fixed. So i continue the boot normally.

I ran df -h, when i was already in kubuntu, it shows /dev/sda1 with 25G now, but sda3 isnt recognized. I booted with PartedMagic and sda3 is there.

---

### Post by bodhi.zazen on 2008-02-22
We probably need to update fstab.

You can see this link :

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

If you need help we need to boot to ubuntu and show us:

```
sudo fdisk -l
```

And the current contents of /etc/fstab

```
gksu gedit /etc/fstab
```

---

### Post by AndreSantos on 2008-02-22
fdisk -l
```
Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cilindros of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000568f9

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/sda1   *           1        3187    25599546   83  Linux
/dev/sda2            9454        9729     22
16970   82  Linux swap / Solaris
/dev/sda3            3188        9453    50331645   83  Linux

Partições lógicas fora da ordem do disco
```

The last line is translated to en as: "Logical partitions not on disk order". (something like that).

my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0d4d7afd-e030-4e13-8b8b-91be9246afd0 /               reiserfs notail          0       1
# /dev/sda3
UUID=ba9c492f-64e5-4e69-a045-9425b0302704 /media/sda3     reiserfs defaults        0       2
# /dev/sda2
UUID=de76964d-1ce9-49a3-9b72-37cd605e421a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Im going to read the link you gave me now, thanks for the info.

---

### Post by AndreSantos on 2008-02-22
Can i get some help here? I dont really know what to do next...i read the link but im not sure what to do next.

---

### Post by bodhi.zazen on 2008-02-22
Sorry. My guess is the UUID may have changed, not sure.

Yea, when you created sda3 the UUID changed.

So you can either change UUID=xxx.yyy.zzz to sda3 in /etc/fstab, like this:

> # /dev/sda3
/dev/sda3 /media/sda3     reiserfs defaults        0       2

OR list your partitions with :

```
sudo blkid
``` and update the UUID number of sda3 in fstab.

---

### Post by AndreSantos on 2008-02-22
Very well, it worked fine now. Now some general question... Do u think i should mount sda3 as /home ?

---

### Post by bodhi.zazen on 2008-02-22
I think you should keep your data separate from your operating system.

A separate home is easy, personally I use a data partition.

At any rate, if you want to move /home, follow a guide, like these:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by AndreSantos on 2008-02-23
Thanks again, i think thats all!

---

