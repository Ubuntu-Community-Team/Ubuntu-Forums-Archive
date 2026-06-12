---
title: "Automount?"
date: 2008-02-07
forum: General Help
---

### Post by synth7 on 2008-02-07
In Ubuntu 7.10 I can see my Windows "drive" in /media/System/ (System is the name of the partition in Windows). I have a few links to my Windows share that I want to have in Ubuntu, but after every boot up I have to manually navigate to /media/System/ to get those links to work, or else the folders will just show up as broken links. How can I have /media/System/ "auto-mount" on startup, or is there something else I should do?

I looked in the threads it suggested based on this thread topic but I didn't see anything that really helped.

Thanks

---

### Post by taurus on 2008-02-07
You need to add an entry in /etc/fstab for your ntfs partition if you want to mount it automatically each time you boot Ubuntu.  Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by synth7 on 2008-02-07
```

jsz@lapt0p:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e045244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13036   104704102    7  HPFS/NTFS
/dev/sda2           13037       19189    49423972+  83  Linux
/dev/sda3           19190       19457     2152710    5  Extended
/dev/sda5           19190       19457     2152678+  82  Linux swap / Solaris

```

```

jsz@lapt0p:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=0bc6d2cd-6412-415d-97db-3e6651f17dd0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=db40579e-a1c3-4f3a-b56d-27d8955f6b4e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

```

jsz@lapt0p:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              47G  3.1G   42G   7% /
varrun               1014M   92K 1013M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   96K 1013M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   34M  980M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1             100G   18G   83G  18% /media/System

```

---

### Post by taurus on 2008-02-07
First, unmount your ntfs partition.

```
sudo umount /media/System
```
Then, edit /etc/fstab 

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda1   /media/System   ntfs-3g   defaults   0   0
```
Save it.  Then, install ntfs-3g driver, create a new mount point, and mount it.

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/System
sudo mount -a
df -h
```

---

### Post by synth7 on 2008-02-07
Thanks for the quick replies, that did it

---

### Post by bwtranch on 2008-02-07
That was very good taurus and since they didn't thank you. I will.:)

---

### Post by LeDechaine on 2008-02-09
Hmm, same problem for me, but mine's a bit more complex.
I had two hard drives, one mainly for XP + Programs, the other for data, with two partitions. Haven't took any chances, I simply unplugged the data disk before trying to install Ubuntu on the hard drive with XP on, on another partition (dual boot).

So, briefly:
**Hard Drive 1:**
Partition 1: XP
Partition 2: Ubuntu
**Hard Drive 2:**
Partition 1: Personnel (Personal data)
Partition 2: Audiovisuel (Audio-video data)

But now, I plugged the 2nd hard drive, but the two partitions on the hard drive 2 (Personnel + Audiovisuel) are not automatically mounting. (Well, not sure about the second, 'cause I honestly don't remember, but the "Personnel" partition is not "automounting" for sure.)

Here's my:
```
sudo fdisk -l
cat /etc/fstab
df -h
```

**sudo fdisk -l:**
```
Disque /dev/hda: 120.0 Go, 120034123776 octets
255 heads, 63 sectors/track, 14593 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf03643c9

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hda1   *           1        6527    52428096    c  W95 FAT32 (LBA)
/dev/hda2            6528       13887    59119200    f  W95 Etendu (LBA)
/dev/hda5            6528       13054    52428096    b  W95 FAT32
/dev/hda6           13156       13279      995998+  82  Linux swap / Solaris
/dev/hda7           13280       13887     4883728+  83  Linux

Disque /dev/hdb: 120.0 Go, 120034123776 octets
255 heads, 63 sectors/track, 14593 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7593f182

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hdb1   *           1       12635   101490606    c  W95 FAT32 (LBA)
/dev/hdb2           12636       14593    15727635    f  W95 Etendu (LBA)
/dev/hdb5           12636       14593    15727603+   b  W95 FAT32

```

**cat /etc/fstab**:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda7
UUID=d8e4bc4e-3ae1-492c-bc14-953fece52910 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=3E5D-0B07  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/hda5
UUID=4230-2AE9  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/hda6
UUID=1f9e10a6-297c-406b-97c4-6c3d4a8666cb none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

**df -h**
```
Sys. de fich.            Tail. Occ. Disp. %Occ. Monté sur
/dev/hda7             4,6G  4,2G  214M  96% /
varrun                157M   88K  157M   1% /var/run
varlock               157M  4,0K  157M   1% /var/lock
udev                  157M   92K  157M   1% /dev
devshm                157M     0  157M   0% /dev/shm
lrm                   157M   34M  123M  22% /lib/modules/2.6.22-14-generic/volatile
/dev/hda1              50G   50G  953M  99% /media/hda1
/dev/hda5              50G   48G  2,0G  97% /media/hda5
/dev/hdb5              15G   15G  448M  98% /media/PERSONNEL
/dev/hdb1              97G   96G  854M 100% /media/AUDIOVISUEL
```

*So, basically, i'd have to add..:*
```
/dev/hdb1 /media/Audiovisuel     vfat    defaults
/dev/hdb5 /media/Personnel     vfat    defaults
```
..At the end of my /etc/fstab file (well, before the CD and floppy)?

I'm not sure about the "**UUID**" things and if i have to write "**defaults,utf8,umask=007,gid=46**", so i'm asking you. ;)

Thanks in advance! :)

---

### Post by LeDechaine on 2008-02-09
Okay now i've just RTFM ;)

'seems that **defaults,utf8,umask=007,gid=46** won't cause any harm..
i don't know what **umask=007** means (the 007 number), i'm assuming that **gid=46** is ledechaine (me ;)), since everything worked fine until now..

*supper, brb* :)

---

### Post by mikewhatever on 2008-02-09
> **LeDechaine said:**
> Okay now i've just RTFM ;)

'seems that **defaults,utf8,umask=007,gid=46** won't cause any harm..
i don't know what **umask=007** means (the 007 number), i'm assuming that **gid=46** is ledechaine (me ;)), since everything worked fine until now..

*supper, brb* :)

That should work fine. Just to clarify, umask=007 means you and your group have full permissions, but no other user does; gid=46 should be one of the groups you belong to, plugdev or something.

---

### Post by LeDechaine on 2008-02-09
Thanks :) Tryin' it.

(Well, adding it. I'll see if it works at the next reboot.)
..But if it doesn't i'm screwed. :D (Whatever, at worst, my poor, left alone, and solitary windows operetaing system will be helpful to get back here in the forums ;))

---

### Post by mikewhatever on 2008-02-09
> **LeDechaine said:**
> Thanks :) Tryin' it.

(Well, adding it. I'll see if it works at the next reboot.)
..But if it doesn't i'm screwed. :D (Whatever, at worst, my poor, left alone, and solitary windows operetaing system will be helpful to get back here in the forums ;))

Actually, I thought you've done that already and it worked, but anyway, if anything goes wrong with those settings, boot into recovery mode (second option in grub menu), login and edit fstab through command line. To get to it, use nano text editor, <sudo nano /etc/fstab>, press ctrl+x to save the changes. Then use something tested --> [http://psychocats.net/ubuntu/mountwindows#fat32](http://psychocats.net/ubuntu/mountwindows#fat32)

---

### Post by LeDechaine on 2008-02-09
My fstab, modified via gedit, now looks like that:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda7
UUID=d8e4bc4e-3ae1-492c-bc14-953fece52910 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=3E5D-0B07  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/hda5
UUID=4230-2AE9  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/hda6
UUID=1f9e10a6-297c-406b-97c4-6c3d4a8666cb none            swap    sw              0       0
/dev/hdb1       /media/audiovisuel     vfat    defaults,utf8,umask=007,gid=46 0 0
/dev/hdb5       /media/personnel       vfat    defaults,utf8,umask=007,gid=46 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

Haven't rebooted yet, so I can still edit the file if there is errors. If I screwed up anything, tell me! ;)

---

### Post by LeDechaine on 2008-02-15
Err, well, looks like i screwed up something finally, because I don't even *see* the 2 partitions of the second drive now. (And yes, the drive is plugged, and the 2 partitions are there! ;))

```
/dev/hdb1       /media/audiovisuel     vfat    defaults,utf8,umask=007,gid=46 0 0
/dev/hdb5       /media/personnel       vfat    defaults,utf8,umask=007,gid=46 0 0
```
looks like these lines were ignored... and well.. even prevented the "drives" (the drive, the 2 partitions) to be visible in nautilus.

Before modifying this fstab file I was able to mount the 2 partitions by double-clicking on their icons in nautilus. Now I don't even see them.

I'm not gonna try any commands like **df -h** or anything like that now because, well, first, I'll wait for your help, and second, it's nearly 6AM here and I haven't slept yet (night owl here), so i'm a little bit asleep, therefore i won't open the terminal, 'cause I don't want my system to get worse! :D

Thanks in advance. ;)

---

### Post by LeDechaine on 2008-02-15
Err, help. :p

How do I correct this?

---

### Post by LeDechaine on 2008-02-16
So, **df -h** (obviously) doesn't shows my *hdb1* and *hdb5* partitions.
But **fdisk -l** shows them both. I assume that this is an fstab configuration problem, i.e.: I screwed it up :P

*So...*
Does changing this:
```
/dev/hdb1       /media/audiovisuel     vfat    defaults,utf8,umask=007,gid=46 0 0
/dev/hdb5       /media/personnel       vfat    defaults,utf8,umask=007,gid=46 0 0
```

To this:
```
/dev/hdb1       /media/audiovisuel     vfat    defaults
/dev/hdb5       /media/personnel       vfat    defaults
```

Can solve my problem?
Any help/advices welcome.

---

### Post by LeDechaine on 2008-02-16
Hey, I need help, there's nearly 120GB of stuff I don't want to lose in there, so I don't want to screw up anything, and I also don't want to try things blindly, so if anybody can tell me if yes or no, the modification of the previous post is **safe** and, above all, will *work*, **let's go!**

---

### Post by LeDechaine on 2008-02-17
Nevermind. Problem solved. :)

I'm an idiot. Haha. **mount -a** showed me that the mount points were inexistant.
Forgot to create the "audiovisuel" and "personnel" directories before =/

Anyway. Thanks everyone. :)

---

