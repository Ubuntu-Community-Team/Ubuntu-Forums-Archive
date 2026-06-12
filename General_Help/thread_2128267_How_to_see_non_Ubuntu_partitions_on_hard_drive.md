---
title: "How to see non Ubuntu partitions on hard drive"
date: 2013-03-22
forum: General Help
---

### Post by Docfxit on 2013-03-22
I have a multi boot PC.  Ubuntu is on one of the partitions and has no free space.  I have another partition on the hard drive.  How can I see the other partition to copy some files to it?

I have tried:
df -h
That shows me:
/dev/sda2

So I know Ubuntu is in the second partition.
I tried 
CD /dev/
It says CD command not found.
It's running ver. 7.1

Thanks,

Docfxit

---

### Post by SgtHubcap on 2013-03-22
You need to mount them to first. There are various ways to mount partitions

btw the CD command is

```
 $ cd /dev
$ ls
```

Alternatively, you could grab the UUID for the partition, add it to your fstab and mount on boot up.

First you're going to want to make a mount directory preferably in /media. Some like it in /mnt its all preference.
For this Ill use /media with the mount point /Windows adsda 
 
1:```
$ sudo mkdir /media/Windows
```

2:```
$ sudo blkid
```


3:copy the UUID with in the quotation marks of the partition your want to mount.

4:```
$ sudo gedit /ect/fstab
```

5:add line
```
#Windows Partition 
UUID=insert UUID                     /media/Windows      ntfs  defaults,umask=007,gid=46 0 0

```

6:Save,exit or go to Terminal press ctrl+c

7:```
$ Sudo reboot
```

---

### Post by Tavin on 2013-03-22
usually all drives show up in the Filemanagers righthand panel, and you can mount them by simply klciking on them. Does this work?

---

### Post by Docfxit on 2013-03-22
I set terminal to root and then CD started working.  This is what I got:

```
root@UbuntuAsterisk:~# cd /dev
root@UbuntuAsterisk:/dev# ls
4-1        ptyd0  ptys9  ptyy2       tty29  ttycf  ttys4  ttyxd
4-2        ptyd1  ptysa  ptyy3       tty3   ttyd0  ttys5  ttyxe
4-2.1      ptyd2  ptysb  ptyy4       tty30  ttyd1  ttys6  ttyxf
adsp       ptyd3  ptysc  ptyy5       tty31  ttyd2  ttys7  ttyy0
audio      ptyd4  ptysd  ptyy6       tty32  ttyd3  ttys8  ttyy1
bus        ptyd5  ptyse  ptyy7       tty33  ttyd4  ttys9  ttyy2
cdrom1     ptyd6  ptysf  ptyy8       tty34  ttyd5  ttysa  ttyy3
cdrw1      ptyd7  ptyt0  ptyy9       tty35  ttyd6  ttysb  ttyy4
console    ptyd8  ptyt1  ptyya       tty36  ttyd7  ttysc  ttyy5
core       ptyd9  ptyt2  ptyyb       tty37  ttyd8  ttysd  ttyy6
dahdi      ptyda  ptyt3  ptyyc       tty38  ttyd9  ttyse  ttyy7
disk       ptydb  ptyt4  ptyyd       tty39  ttyda  ttysf  ttyy8
dsp        ptydc  ptyt5  ptyye       tty4   ttydb  ttyt0  ttyy9
dvd1       ptydd  ptyt6  ptyyf       tty40  ttydc  ttyt1  ttyya
dvdrw1     ptyde  ptyt7  ptyz0       tty41  ttydd  ttyt2  ttyyb
fd         ptydf  ptyt8  ptyz1       tty42  ttyde  ttyt3  ttyyc
fd0        ptye0  ptyt9  ptyz2       tty43  ttydf  ttyt4  ttyyd
full       ptye1  ptyta  ptyz3       tty44  ttye0  ttyt5  ttyye
fuse       ptye2  ptytb  ptyz4       tty45  ttye1  ttyt6  ttyyf
hpet       ptye3  ptytc  ptyz5       tty46  ttye2  ttyt7  ttyz0
initctl    ptye4  ptytd  ptyz6       tty47  ttye3  ttyt8  ttyz1
input      ptye5  ptyte  ptyz7       tty48  ttye4  ttyt9  ttyz2
kmem       ptye6  ptytf  ptyz8       tty49  ttye5  ttyta  ttyz3
kmsg       ptye7  ptyu0  ptyz9       tty5   ttye6  ttytb  ttyz4
log        ptye8  ptyu1  ptyza       tty50  ttye7  ttytc  ttyz5
loop0      ptye9  ptyu2  ptyzb       tty51  ttye8  ttytd  ttyz6
lp0        ptyea  ptyu3  ptyzc       tty52  ttye9  ttyte  ttyz7
MAKEDEV    ptyeb  ptyu4  ptyzd       tty53  ttyea  ttytf  ttyz8
mem        ptyec  ptyu5  ptyze       tty54  ttyeb  ttyu0  ttyz9
mixer      ptyed  ptyu6  ptyzf       tty55  ttyec  ttyu1  ttyza
net        ptyee  ptyu7  ram0        tty56  ttyed  ttyu2  ttyzb
null       ptyef  ptyu8  ram1        tty57  ttyee  ttyu3  ttyzc
nvidia0    ptyp0  ptyu9  ram10       tty58  ttyef  ttyu4  ttyzd
nvidiactl  ptyp1  ptyua  ram11       tty59  ttyp0  ttyu5  ttyze
oldmem     ptyp2  ptyub  ram12       tty6   ttyp1  ttyu6  ttyzf
parport0   ptyp3  ptyuc  ram13       tty60  ttyp2  ttyu7  urandom
port       ptyp4  ptyud  ram14       tty61  ttyp3  ttyu8  usb1
ppp        ptyp5  ptyue  ram15       tty62  ttyp4  ttyu9  usb2
psaux      ptyp6  ptyuf  ram2        tty63  ttyp5  ttyua  usb3
ptmx       ptyp7  ptyv0  ram3        tty7   ttyp6  ttyub  usb4
pts        ptyp8  ptyv1  ram4        tty8   ttyp7  ttyuc  usb5
ptya0      ptyp9  ptyv2  ram5        tty9   ttyp8  ttyud  usb6
ptya1      ptypa  ptyv3  ram6        ttya0  ttyp9  ttyue  usb7
ptya2      ptypb  ptyv4  ram7        ttya1  ttypa  ttyuf  usbdev1.1_ep00
ptya3      ptypc  ptyv5  ram8        ttya2  ttypb  ttyv0  usbdev1.1_ep81
ptya4      ptypd  ptyv6  ram9        ttya3  ttypc  ttyv1  usbdev2.1_ep00
ptya5      ptype  ptyv7  random      ttya4  ttypd  ttyv2  usbdev2.1_ep81
ptya6      ptypf  ptyv8  rtc         ttya5  ttype  ttyv3  usbdev3.1_ep00
ptya7      ptyq0  ptyv9  scd0        ttya6  ttypf  ttyv4  usbdev3.1_ep81
ptya8      ptyq1  ptyva  sda         ttya7  ttyq0  ttyv5  usbdev4.1_ep00
ptya9      ptyq2  ptyvb  sda1        ttya8  ttyq1  ttyv6  usbdev4.1_ep81
ptyaa      ptyq3  ptyvc  sda2        ttya9  ttyq2  ttyv7  usbdev4.3_ep00
ptyab      ptyq4  ptyvd  sda3        ttyaa  ttyq3  ttyv8  usbdev4.3_ep81
ptyac      ptyq5  ptyve  sda4        ttyab  ttyq4  ttyv9  usbdev4.4_ep00
ptyad      ptyq6  ptyvf  sequencer   ttyac  ttyq5  ttyva  usbdev4.4_ep81
ptyae      ptyq7  ptyw0  sequencer2  ttyad  ttyq6  ttyvb  usbdev4.5_ep00
ptyaf      ptyq8  ptyw1  sg0         ttyae  ttyq7  ttyvc  usbdev4.5_ep81
ptyb0      ptyq9  ptyw2  sg1         ttyaf  ttyq8  ttyvd  usbdev4.5_ep82
ptyb1      ptyqa  ptyw3  shm         ttyb0  ttyq9  ttyve  usbdev5.1_ep00
ptyb2      ptyqb  ptyw4  snapshot    ttyb1  ttyqa  ttyvf  usbdev5.1_ep81
ptyb3      ptyqc  ptyw5  snd         ttyb2  ttyqb  ttyw0  usbdev6.1_ep00
ptyb4      ptyqd  ptyw6  sndstat     ttyb3  ttyqc  ttyw1  usbdev6.1_ep81
ptyb5      ptyqe  ptyw7  sr0         ttyb4  ttyqd  ttyw2  usbdev7.1_ep00
ptyb6      ptyqf  ptyw8  stderr      ttyb5  ttyqe  ttyw3  usbdev7.1_ep81
ptyb7      ptyr0  ptyw9  stdin       ttyb6  ttyqf  ttyw4  vcs
ptyb8      ptyr1  ptywa  stdout      ttyb7  ttyr0  ttyw5  vcs1
ptyb9      ptyr2  ptywb  tty         ttyb8  ttyr1  ttyw6  vcs2
ptyba      ptyr3  ptywc  tty0        ttyb9  ttyr2  ttyw7  vcs3
ptybb      ptyr4  ptywd  tty1        ttyba  ttyr3  ttyw8  vcs4
ptybc      ptyr5  ptywe  tty10       ttybb  ttyr4  ttyw9  vcs5
ptybd      ptyr6  ptywf  tty11       ttybc  ttyr5  ttywa  vcs6
ptybe      ptyr7  ptyx0  tty12       ttybd  ttyr6  ttywb  vcs7
ptybf      ptyr8  ptyx1  tty13       ttybe  ttyr7  ttywc  vcs8
ptyc0      ptyr9  ptyx2  tty14       ttybf  ttyr8  ttywd  vcs9
ptyc1      ptyra  ptyx3  tty15       ttyc0  ttyr9  ttywe  vcsa
ptyc2      ptyrb  ptyx4  tty16       ttyc1  ttyra  ttywf  vcsa1
ptyc3      ptyrc  ptyx5  tty17       ttyc2  ttyrb  ttyx0  vcsa2
ptyc4      ptyrd  ptyx6  tty18       ttyc3  ttyrc  ttyx1  vcsa3
ptyc5      ptyre  ptyx7  tty19       ttyc4  ttyrd  ttyx2  vcsa4
ptyc6      ptyrf  ptyx8  tty2        ttyc5  ttyre  ttyx3  vcsa5
ptyc7      ptys0  ptyx9  tty20       ttyc6  ttyrf  ttyx4  vcsa6
ptyc8      ptys1  ptyxa  tty21       ttyc7  ttys0  ttyx5  vcsa7
ptyc9      ptys2  ptyxb  tty22       ttyc8  ttyS0  ttyx6  vcsa8
ptyca      ptys3  ptyxc  tty23       ttyc9  ttys1  ttyx7  vcsa9
ptycb      ptys4  ptyxd  tty24       ttyca  ttyS1  ttyx8  watchdog
ptycc      ptys5  ptyxe  tty25       ttycb  ttys2  ttyx9  xconsole
ptycd      ptys6  ptyxf  tty26       ttycc  ttyS2  ttyxa  zero
ptyce      ptys7  ptyy0  tty27       ttycd  ttys3  ttyxb
ptycf      ptys8  ptyy1  tty28       ttyce  ttyS3  ttyxc
```

When I open the file manager that I normally use (Double Commander - Root Privileges) it shoes sda1 on the top. When I select it I get a message saying "Disk is not available"
I believe that is the first partition.  How can I make it available?

Thanks,

Docfxit

---

### Post by oldos2er on 2013-03-22
Linux is case-sensitive, so use cd not CD.

```
sudo fdisk -l
``` will show all hard disks and their partitions.

---

### Post by Docfxit on 2013-03-22
```

fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6ef67c30

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3480    27952076   17  Hidden HPFS/NTFS
/dev/sda2   *        3481        4221     5952082+  83  Linux
/dev/sda3           28753       28995     1951897+  92  Unknown
/dev/sda4           28996       30402    11295744   1c  Hidden W95 FAT32 (LBA)
Partition 4 does not end on cylinder boundary.

```

---

### Post by Docfxit on 2013-03-22
SgtHubcap 

Please give me an example of item # 3

Thanks,

Docfxit

---

### Post by SgtHubcap on 2013-03-22
```
sudo blkid
```

Copy and paste.Here

Well, i overlooked an issue with what your trying to do but i think this might help

[http://www.howtogeek.com/60817/how-to-auto-mount-partitions-at-linux-startup-the-easy-way/](http://www.howtogeek.com/60817/how-to-auto-mount-partitions-at-linux-startup-the-easy-way/)

---

### Post by Docfxit on 2013-03-22
SgtHubcap 

Thank you for all your instructions.  I have followed all your instructions.  After re-booting I now see a drive called Windows.  When I select it I get "Disk is not available"

Thank you,

Docfxit

---

### Post by Docfxit on 2013-03-22
I don't have any space to install the program pysdm.

I keep deleting files but no free space is showing.  Does the deleted files go to a recycle bin and that's why deleting files doesn't free up space?  How can I clean out the recycle bin?

```

root@UbuntuAsterisk:~# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2              5858544   5782668         0 100% /
varrun                  517148       200    516948   1% /var/run
varlock                 517148         0    517148   0% /var/lock
udev                    517148        92    517056   1% /dev
devshm                  517148         0    517148   0% /dev/shm
lrm                     517148     34696    482452   7% /lib/modules/2.6.22-15-generic/volatile
overflow                  1024        56       968   6% /tmp

```

I have run this to find trash folders:
sudo find / -type d -name *Trash* 

It displayed /home/docfxit/.Trash

I used this to clean it out:
gksudo nautilus /home/docfxit/.Trash

There wasn't anything in there.

Thanks,

Docfxit

---

### Post by oldos2er on 2013-03-22
Pysdm was removed from the repositories because it's no longer maintained, and doesn't support ext4, among other problems.

See [this thread]("http://ubuntuforums.org/showthread.php?t=1122670") for tips on freeing hard disk space.

---

