---
title: "Can't access my shared fat32 partition from Ubuntu"
date: 2008-06-09
forum: General Help
---

### Post by Temmex on 2008-06-09
G'day guys

I've just made my laptop a dual boot xp/ubuntu system, with what seems a pretty normal setup of an ntfs windows partition, a linux ext3 partition, a linux swap, and a fat32 'shared' partition. There is also a windows backup sort of partition put on there by acer, but thats not touched by anything.

My problem is that ubuntu can't actually see the fat32 partition when it comes to managing files, but i can see it now from windows.  In theory shouldnt fat32 be fine for both?

I've never really had much of an experience with Ubuntu, but with my PC which has been dual boot for a long time it works fine. I dont know if i have to move partitions, mount, or anything right now.

Any help would be great

T

---

### Post by lisati on 2008-06-09
(Deleted: didn't read the question properly!)

---

### Post by Temmex on 2008-06-09
aw i got all excited too :(

---

### Post by VMC on 2008-06-09
> **Temmex said:**
> G'day guys

I've just made my laptop a dual boot xp/ubuntu system, with what seems a pretty normal setup of an ntfs windows partition, a linux ext3 partition, a linux swap, and a fat32 'shared' partition. There is also a windows backup sort of partition put on there by acer, but thats not touched by anything.

My problem is that ubuntu can't actually see the fat32 partition when it comes to managing files, but i can see it now from windows.  In theory shouldnt fat32 be fine for both?

I've never really had much of an experience with Ubuntu, but with my PC which has been dual boot for a long time it works fine. I dont know if i have to move partitions, mount, or anything right now.

Any help would be great

T

Output '/etc/fstab' so we can see what wants to be mounted.

---

### Post by Temmex on 2008-06-09
It seems i can access it from my disk usage analyzer actually, but i cant see it in the computer folder where my other partitions are visible, or on directory menu's like those in media players.

Looks like my problem has changed, but can anyone see what i've done wrong, or haven't done?

---

### Post by Temmex on 2008-06-09
> **VMC said:**
> Output '/etc/fstab' so we can see what wants to be mounted.

I'm not too cluey at this yet, but how do i do that?

---

### Post by VMC on 2008-06-09
> **Temmex said:**
> I'm not too cluey at this yet, but how do i do that?

Open a terminal Applications > Accessories > Terminal. Then type:
cat /etc/fstab

You should see a line that says something in the order of:
/dev/hdXN /mount/point vfat defaults 0 0

Go here for a better explaination:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
Make sure you read the part about Fat32.

---

### Post by Temmex on 2008-06-09
> **VMC said:**
> Open a terminal Applications > Accessories > Terminal. Then type:
cat /etc/fstab

You should see a line that says something in the order of:
/dev/hdXN /mount/point vfat defaults 0 0

Go here for a better explaination:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
Make sure you read the part about Fat32.
ah thankyou ill have a squiz over it now, thanks for your help :)

---

### Post by Temmex on 2008-06-09
also,  cat /etc/fstab comes up with

>  # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=6c982cd0-433d-4386-a342-268e233a74e4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=7A3C-B631  /share          vfat    utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=4cb6263e-47b2-4df4-9c12-8b1164fb92c6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



not sure what it means unfortunately :(

---

### Post by VMC on 2008-06-09
Next type from a Terminal

```
sudo fdisk -l
```(that 'l' is 'L' lower case)

That way we can find your vfat partitions.

---

### Post by Temmex on 2008-06-09
sudo f-disk -l returns:

> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8f0ffa4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     5116671   12  Compaq diagnostics
/dev/sda2   *         638        5435    38539935    7  HPFS/NTFS
/dev/sda3            9796       14593    38539935    f  W95 Ext'd (LBA)
/dev/sda4            5436        9795    35021700   83  Linux
/dev/sda5            9796       10057     2104483+  82  Linux swap / Solaris
/dev/sda6           10058       14593    36435388+   b  W95 FAT32



---

### Post by Temmex on 2008-06-09
I feel very stupid, it's all there under my /share. I must have just done something on my PC that made it visible alongside my dvd drive and windows partition, which is where i was looking for it.

If theres a way to do that ill look it up, so I stop wasting your time :)

sorry, and thankyou again! 

T

---

### Post by Barriehie on 2008-06-09
> sudo f-disk -l returns:

                                                      Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8f0ffa4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     5116671   12  Compaq diagnostics
/dev/sda2   *         638        5435    38539935    7  HPFS/NTFS
/dev/sda3            9796       14593    38539935    f  W95 Ext'd (LBA)
/dev/sda4            5436        9795    35021700   83  Linux
/dev/sda5            9796       10057     2104483+  82  Linux swap / Solaris
/dev/sda6           10058       14593    36435388+   b  W95 FAT32
Okay, sda6 is your 'invisible' FAT32 partition.  You'll have to add a line to the end of your fstab file and create a directory to be used as a mount point.  I have my windows mount point directory named **disk** and the path is **/home/barrie/disk, **you can call it whatever you want, keep it simple.  You have to have root permission to edit the fstab file and you can do that by going to a terminal and entering in **sudo gedit /etc/fstab **and enter your password when prompted.  Now, go to the end of your fstab file and put in this line:

```

/dev/sda6 */your path to the mount point dir/ *auto rw,auto,exec,user 0 0 

```That should automount the partition at boot time; which you'll have to do for the changes to your fstab file to take effect.

Barrie

---

### Post by VMC on 2008-06-09
From "Applications > Accessories > Terminal" type this:
```
sudo mkdir /mnt/fat
```
If that completes with no errors, type:

```
sudo gedit /etc/fstab
```
go the the end and add this line:

```
/dev/sda6  /mnt/fat vfat user,umask=000 0 0
```

Save it. Then reboot.

---

