---
title: "Resize Linux partition without formatting...?"
date: 2006-12-03
forum: General Help
---

### Post by gejr on 2006-12-03
So I've become quite fond of Ubuntu now and I want to make the ext3 partition bigger. Is this possible without reformatting? I'd really like to keep all the modifications I've done till now. 

According to "df -h" this is my partitions as it is:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              11G  8.8G 1018M  90% /
varrun                244M   96K  244M   1% /var/run
varlock               244M     0  244M   0% /var/lock
procbususb             10M  116K  9.9M   2% /proc/bus/usb
udev                   10M  116K  9.9M   2% /dev
devshm                244M     0  244M   0% /dev/shm
lrm                   244M   18M  227M   8% /lib/modules/2.6.17-10-generic/volatile
/dev/disk/by-uuid/AC38AE4B38AE147C
                       16G   15G  1.3G  93% /media/sda1
/dev/scd0             626M  626M     0 100% /media/cdrom0
```

I would like to leave about 7-8 gb for Windows, and move the rest of the gb's to my linux partition. Formatting the Windows-partition is no problem, it's the Linux partition I'm afraid to lose.

Any hints/help on this? Have anyone either done something similar to this?
Is it even possible?

Thanks!

---

### Post by dmartinsca on 2006-12-03
You can do this rather easily, although there is always a chance something could go wrong, so you should backup your data first if possible. (I've never actually lost any data while resizing partitions but there's always that slight chance).
Anyways, i'd recommend [gparted.]("http://gparted.sourceforge.net") It's only about a 30MB download for either a live cd or live usb image to boot your computer from & it gives you a nice graphical interface. It's important that the partitions you're altering aren't in use while making the changes, which is why you'll need a live cd(or usb) of some type.

---

### Post by gejr on 2006-12-04
Thanks, but I didn't do this right I think!

I did something, but not what I wanted. Checkout my "fdisk -l":
[HTML]Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2014    16177423+  83  Linux
/dev/sda2            2015        3381    10980427+  83  Linux
/dev/sda3            4685        4864     1445850    5  Extended
/dev/sda4   *        3382        4684    10466347+  83  Linux
/dev/sda5            4745        4864      963868+  82  Linux swap / Solaris
/dev/sda6            4685        4744      481887   82  Linux swap / Solaris

Partition table entries are not in disk order[/HTML]

And my df -h:
[HTML]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              11G  8.9G  968M  91% /
varrun                244M   96K  244M   1% /var/run
varlock               244M     0  244M   0% /var/lock
procbususb             10M  116K  9.9M   2% /proc/bus/usb
udev                   10M  116K  9.9M   2% /dev
devshm                244M     0  244M   0% /dev/shm
lrm                   244M   18M  227M   8% /lib/modules/2.6.17-10-generic/volatile[/HTML]

Doesn't that look extremely messy?
I want it to be like this:
/dev/sda1/ 33gb Linux
/dev/sda2/ 5gb Windows
/dev/sda3/ Swap

Do I need any of the other partitions ? Is it possible to make the table look like this with GParted? I didn't find an option to like "merge", but I guess I could delete partitions and resize another one to take it's place.

/dev/sda4/ was flagged with "boot" in gparted..which kinda made me decide not to delete it, although it's a 10gb partition I don't really know what's for. I have never used that sda4 partition as I'm aware of, only sda1 & 2.

Long post..hope someone takes time to read it.. :)

---

### Post by gejr on 2006-12-04
Ok.. I've managed to do some modifications. My question now is, what is this 10gb partition for? It is flagged with "boot" so I haven't dared removing it.  Too afraid of messing up this Ubuntu installation.

Anyway, I would really like to be able to use these 10 gb. On a tiny 40gb laptop harddisk 10gb is a big deal. How can I access them? Is it safe to remove them and move the boot flag to my main sda2-partition, or will that cause my computer to not boot?

[HTML]geo@box:/media$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1        3381    27157851   83  Linux
/dev/sda3            4685        4864     1445850    5  Extended
/dev/sda4   *        3382        4684    10466347+  83  Linux
/dev/sda5            4745        4864      963868+  82  Linux swap / Solaris

Partition table entries are not in disk order[/HTML]

---

### Post by dmartinsca on 2006-12-04
try to mount it and see what is there... **sudo mkdir /mnt/tmp; sudo mount /dev/sda4 /mnt/tmp**

Linux doesn't care about the boot flag, this is a stupid DOS/windows thing so  my guess would be that sda4 is your windows partition. Also, according to the Start & End columns, the disk is arranged kind of like this:

```
sda2
sda4
sda3 (contains the following)
     free space
     sda5
```

---

### Post by gejr on 2006-12-04
weird,, I've tried a lot of different types to mount it. But none of them work. Only doing "sudo mount /dev/sda4 /mnt/asdf/" gives me "You must specify filesystem type." :S

---

