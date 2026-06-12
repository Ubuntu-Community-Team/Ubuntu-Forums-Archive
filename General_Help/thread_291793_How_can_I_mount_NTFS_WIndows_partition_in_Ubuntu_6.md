---
title: "How can I mount NTFS WIndows partition in Ubuntu 6.10 Edgy?"
date: 2006-11-02
forum: General Help
---

### Post by ubuntu27 on 2006-11-02
Yesterday I've installed Edy over Breezy (since Breezy game me a headache, and there was not enough space in ext3)

Anyway, something I've learned in Breezy is not useful in Edgy :-k  
Like how to mount NTFS partition.

In Breezy, I could mount using the terminal or using an application called "Disk Manager" which doesn't exist in Edgy (I have all the repos enabled)

SO basically, I am leaved to use the terminal in edgy. But here is the thing that confuses me:

This is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=4677fc78-aba7-4fbe-9a93-5a61df785d22 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=28bf1d45-4113-439a-89e6-42bb074fcc66 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```



I don't get it, what's all this 

# /dev/hda3
UUID=4677fc78-aba7-4fbe-9a93-5a61df785d22 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=28bf1d45-4113-439a-89e6-42bb074fcc66 none            swap    sw  



about?

Please, help me figure it out how to mount ntfs. thank you.

**Here is the result of fdisk -l**

```
Disk /dev/hda: 120.0 GB, 120060444672 bytes
240 heads, 63 sectors/track, 15508 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         589     4452808+   b  W95 FAT32
/dev/hda2   *         590        8217    57667680    7  HPFS/NTFS
/dev/hda3            8218       15311    53630640   83  Linux
/dev/hda4           15312       15508     1489320    5  Extended
/dev/hda5           15312       15508     1489288+  82  Linux swap / Solaris

```

---

### Post by Polygon on 2006-11-02
you should just be able to specify the filesystem type as "ntfs", but by default that will give you read but not write permissions, for good reason as ntfs write is pretty sketchy.

there are programs like one i read on the fourms today called ntfs-g3 or something along those lines that you can try

but basically mounting it would be

sudo mkdir /media/<name of directory you want to mount in>
sudo mount -t ntfs /dev/<drive> /media/<directory you created>

im not sure what to put in the /etc/fstab file so i wont even try to save you from screwing up cause of my mistake, but those uuid things might be hardware id numbers? all i know is that i got errors about them when i tryed to upgrade and failed miserably.

---

### Post by Cable on 2006-11-02
Read [this]("http://www.psychocats.net/ubuntu/mountwindows").  That will enable to you *read* NTFS partitions.  Writing to NTFS partitions in Linux is still experimental, but possible.  I bet you could find out how here if you really wanted to though.

---

### Post by taurus on 2006-11-02
Just add this line to the end of /etc/fstab...

```

/dev/hda2  /media/windows  ntfs  defaults,umask=0222  0  0

```
Save it and run 

```

sudo mkdir /media/windows
sudo mount -a
df -h

```

---

### Post by ubuntu27 on 2006-11-03
Thank you everyone.

thanks taurus. Looks like I was too paranoid, I though there was a major change. It's the same as with previous versions :D
[B]
df -h[/B]
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              51G  2.0G   46G   5% /
varrun                248M   80K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
procbususb             10M  124K  9.9M   2% /proc/bus/usb
udev                   10M  124K  9.9M   2% /dev
devshm                248M     0  248M   0% /dev/shm
/dev/hda2              55G   45G   11G  81% /media/windows
```

---

### Post by ...acid on 2006-11-04
I'm having a similar problem.  Just different computer.

I would very much like to have my Windows partition to mount upon startup. 
Here are the results of fdisk -l

[HTML]nitro@nitro-desktop:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9352    75119908+  83  Linux
/dev/hdb2            9353        9729     3028252+   5  Extended
/dev/hdb5            9353        9729     3028221   82  Linux swap / Solaris
[/HTML]

---

### Post by ...acid on 2006-11-04
Also, here are the results of /etc/fstab

[HTML]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
# /dev/hda /media/windows ntfs nls=utf8,umask=0222 0 0
UUID=881e4472-7655-4aa1-861e-da8964494206 /               ext3    defaults,erro$
# /dev/hdb5
UUID=1149bffc-fc83-4f76-a605-cf5ec37a4e2d none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
[/HTML]

---

### Post by ...acid on 2006-11-04
I have tried multiple times to get this straight, by reading through other posts, and following the directions similarly.  I hope that I haven't made the system mad at me... Please help.

---

### Post by givré on 2006-11-04
Just uncomment this line :
```
# /dev/hda /media/windows ntfs nls=utf8,umask=0222 0 0
```

EDIT : hum, and i'm not sure /dev/hda will work, this is not a partition name. You should use /dev/hda1 instead

---

### Post by EmyrB on 2006-11-04
I am trying to mount ntfs partitions too so I can access my music, but I am having real difficulties. The out put of fdisk -l is :-

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1305    10482381   42  SFS
/dev/hda2            1306       19929   149597280   42  SFS

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1          65      522081   82  Linux swap / Solaris
/dev/hdb2              66         718     5245222+  83  Linux
/dev/hdb3             719        2023    10482412+  83  Linux
/dev/hdb4            2024        4998    23896687+  83  Linux

I have 4 partitions on my windows box but only 2 show up.

When I issue this command sudo mount -t ntfs /dev/hda2 /media/windows I get the following error - mount: special device /dev/hda2 does not exist

Any ideas?

Cheers
EmyrB

---

### Post by Jason Weiss on 2006-11-04
Hi I am a complete nu bee as well, I am trying read my ntfs drive as well following these instructions.

However I can not save the fstab file. 

i seems I don't have write permissions for /etc maybe 

when I look in properties it says 

"you are not the owner, so you can't change permissions"

---

### Post by taurus on 2006-11-04
DO NOT change permissions of your /etc!!!  If you need to modify something in there, use either sudo or gksudo from a terminal, Applications -> Accessories -> Terminal...

```
sudo nano -Bw /etc/fstab
-or-
gksudo gedit /etc/fstab
```

---

### Post by Cariboo1938 on 2006-11-05
> **Jason Weiss said:**
> Hi I am a complete nu bee as well, I am trying read my ntfs drive as well following these instructions.
However I can not save the fstab file. 
i seems I don't have write permissions for /etc maybe 
when I look in properties it says 
"you are not the owner, so you can't change permissions"
To access /etc/fstab open terminal and use ```
sudo gedit /etc/fstab
``` Enter password if asked.

To access your ntfs drive (allegedly Windows) look [HERE]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=NTFS")
Maybe it helps.

---

### Post by sonoma on 2006-11-28
Thanks Taurus, 
For your succinct instructions:
--------from Taurus---------
Just add this line to the end of /etc/fstab...

Code:

/dev/hda2 /media/windows ntfs defaults,umask=0222 0 0

Save it and run

Code:

sudo mkdir /media/windows 
sudo mount -a 
df -h
------------------
The df -h is a nice touch to see if it worked.

---

### Post by taurus on 2006-11-28
> **sonoma said:**
> Thanks Taurus, 
For your succinct instructions:
--------from Taurus---------
Just add this line to the end of /etc/fstab...

Code:

/dev/hda2 /media/windows ntfs defaults,umask=0222 0 0

Save it and run

Code:

sudo mkdir /media/windows 
sudo mount -a 
df -h
------------------
The df -h is a nice touch to see if it worked.

You're welcome.

---

### Post by auroraborealis on 2006-11-28
If you want to read & write to NTFS, `apt-get ntfs-3g` and substitute it for ntfs in /etc/fstab.

---

### Post by strabes on 2006-11-28
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows)

---

### Post by Wiebelhaus on 2006-12-09
I just can't fathom why i can't get this to work...


"mount: wrong fs type, bad option, bad superblock on /dev/hdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

I have a 160g with Ubuntu installed a 200g cut into three partitions the second partition containing the music.

 sudo fdisk -l

"Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19080   153260068+  83  Linux
/dev/hda2           19081       19457     3028252+   5  Extended
/dev/hda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       10199    81923436    7  HPFS/NTFS
/dev/hdb2           10200       20398    81923467+   7  HPFS/NTFS
/dev/hdb3           20399       24792    35294805    7  HPFS/NTFS"

/dev/hdb2 is the one i want.... man, i'm not off to a good start.

---

