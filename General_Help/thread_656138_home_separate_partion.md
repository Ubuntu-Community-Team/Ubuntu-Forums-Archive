---
title: "/home separate partion"
date: 2008-01-02
forum: General Help
---

### Post by baysideguy on 2008-01-02
Hello I wanted my  /home on a separate partition.

I created a new partition  **/dev/sda3** & created a mount point **media/sda3** and copied all of the old /home files over to media/sda3. However I could not get Gutsy to boot with the **etc/fstab** file mounting the partition & finding the new /home on this new partition.

I tried unsuccessfully a line on the end of fstab to mount the new partion & find /home  **/dev/sda3      media/sda3 /home ext3 nodev,nosuid 0 2** 
This is among numerous other lines of code with help from the following line to mount the partition from fstab **/dev/sda3      media/sda3 ext3 defaults 0 1**   

My solution was to abandon **fstab** pointing to the new /home after it mounts the partition with  **/dev/sda3      media/sda3 ext3 defaults 0 1**. I used a symbolic link created with **ln -s media/sda3/home /home**

I would love to know what line to ad to my fstab file to have Gutsy find /home on the sda3 partition below is as copy of my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ac3cd722-041e-4b27-ba4a-97c3b289392e /              ext3    defaults,errors=remount-ro 0       1

# /dev/sda5
UUID=412f1f1f-b4de-4c42-8c58-bb7c9c7de68c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

/dev/sda3      media/sda3 ext3 defaults 0 1 

Below is df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda1              60G   18G   39G  32% /
varrun                244M   92K  244M   1% /var/run
varlock               244M     0  244M   0% /var/lock
udev                  244M   96K  244M   1% /dev
devshm                244M     0  244M   0% /dev/shm
lrm                   244M   34M  211M  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sda3              87G   15G   68G  18% /media/sda3

Many thanks in advance

---

### Post by capink on 2008-01-02
If I understood your problem correctly, you have to change the following line:

```
/dev/sda3 media/sda3 ext3 defaults 0 1
```

with

```
/dev/sda3 /home ext3 defaults 0 1
```



Another thing you must do is move your old home directory ( if you sure you transfered all it contents to /dev/sda3 ) by typing:

```
sudo mv /home /home_back
```

and create a new empty directory called home

```
sudo mkdir /home
```

Note that the last two steps is not likely to be possible under normal conditions. You will have to do them from a live cd, not from the current installation.


**_Here are the detailed steps:_**

1. Boot your computer from you live cd.
2. Open a terminal and type:

```
mkdir rootfs
```

3. Mount you system on rootfs

```
sudo mount -t ext3 UUID=ac3cd722-041e-4b27-ba4a-97c3b289392e ./rootfs
```

4. Rename your old home directory:

```
sudo mv ./rootfs/home ./rootfs/home_back
```

5. Create a new and empty home directory:

```
sudo mkdir ./rootfs/home
```

6. edit fstab:

```
sudo gedit ./rootfs/etc/fstab
```

and replace the line

```
/dev/sda3 media/sda3 ext3 defaults 0 1
```

with

```
/dev/sda3 /home ext3 defaults 0 1
```

Now you should be finished. But first we want to make sure that you transferred the contents of you old home directory to /dev/sda3

1. Make a new directory called sda3

```
sudo mkdir sda3
```

2. mount your /dev/sda3 on it

```
sudo mount -t ext3 /dev/sda3 ./sda3
```

3. Review the contens of the ./sda3

```
ls ./sda3
```

If you see the normal contents of your home there, you are ok. If not, copy the contents of your old home directory to the new one using:

```
sudo rsync -av ./rootfs/home_back/* ./sda3
```


Now, boot your pc and remove the live cd.

---

### Post by notwen on 2008-01-02
[Here]("http://www.psychocats.net/ubuntu/separatehome") is a guide from Feisty I've used multiple times w/o any issue doing exactly what you're wanting to do.  Everything should work for a Gutsy install as well.  If you try it, please post back should you run into any issues.  Good luck. =]

---

### Post by baysideguy on 2008-01-02
It did not work capink should I be changing 
/dev/sda3 media/sda3 ext3 defaults 0 1

**to **
/dev/sda3/[COLOR="Red"]media/home[/COLOR] /home ext3 defaults 0 1

In order to have the new partition files accessable from ./root/home ?

---

### Post by mdurham on 2008-01-02
I always use a link to another partition, is there any down-side to doing it that way? I've not had any problems.
Cheers, Mike

---

### Post by baysideguy on 2008-01-02
G'day Mike,
No downside with a link at all & it looks like I'm going to be a link guy after all.

It was a good exercise to learn a little more about Ubuntu, but the link jells better with me as a concept.

Clint

---

### Post by dcstar on 2008-01-03
> **mdurham said:**
> I always use a link to another partition, is there any down-side to doing it that way? I've not had any problems.
Cheers, Mike

A link is basically using two filesystems each time you access /home, and AFAIK this doubles any risk (however small) if you suffer a power outage at the time of writing/accessing and also adds a (tiny) overhead for each access.

A direct mount means that all the /home reads and writes are totally separate from your / filesystem, so in the situation of a power outage the separation should make things a bit more resilient.

99.999% of people probably won't experience any difference in operation between the two methods, but (as we all know) if something can go wrong......... :oops:

---

### Post by capink on 2008-01-03
> **baysideguy said:**
> It did not work capink should I be changing 
/dev/sda3 media/sda3 ext3 defaults 0 1

**to **
/dev/sda3/[COLOR="Red"]media/home[/COLOR] /home ext3 defaults 0 1

In order to have the new partition files accessable from ./root/home ?

No. /dev/sda3 is not a file or directory. It is representation of a partition ( I know this is not a very good description). So you cannot append anything to it.

In order to help you more, I need the following information from you:

1. The output of the following commands (from a live cd if you cannot boot your system):

```
sudo blkid
```

```
sudo fdisk -l
```

2. Your username.

3. The contents following files (from your installation):

/etc/fstab
/etc/passwd

you might need to mount you root partition from a live cd to get the contents of these files if your system is umbootable

---

### Post by baysideguy on 2008-01-10
Thanks for the PM Capink
I replaced this line in fstab:

Code:

/dev/sda3 /media/sda3 ext3 defaults 0 1

with this line

Code:

UUID=4a80fd87-78b4-4e9f-84e6-f7a9dc1b17d4       /home            ext3    defaults      0       2

I had an empty /home directory as well but unfortunately it did not boot up, I got the same message that it could not find /home

---

