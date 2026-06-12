---
title: "Low level newbie problem:"
date: 2007-10-27
forum: General Help
---

### Post by wyoming on 2007-10-27
Last time I tried Linux was with Suse 3 or 4 years ago. Had to let go in spite of not liking Win at all. Back with Ubuntu 7.10. And that's a lot better. However, I installed on a 100G partition, leaving a 120 G partition with files, music, videos etc.under XP. During install I checked the migrate settings option. Now my XP partition is unaccessible from boot (it's there but hal.dll is missing) and the content seems to reside in Filesystem/lost+found, which I cannot access (because I'm told I'm not the administrator (?)). I can live without those files, but I'd be happier if I could have access to them (particularly my Thunderbird inbox, Firefox bookmarks and a few sound/video files). Is there a solution or must I forget about it? Thanks!!

---

### Post by taurus on 2007-10-27
You need to mount your Windows partition in Ubuntu before you can access it.  With Gutsy, you can use ntfs-3g driver to even write to it.  First, you need to install it with

```
sudo apt-get update
sudo apt-get install ntfs-3g
```
Then, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add an entry at the bottom of that file for your Windows partition, _assuming_ it's /dev/sda1.

```
/dev/sda1   /media/sda1   ntfs-3g   defaults,locale=en_US.utf8   0   0
```
Save it.  Then, create a mount point and mount it.

```
sudo mkdir /media/sda1
sudo mount -a
df -h
```

---

### Post by wyoming on 2007-10-27
I still have problems and posted aaginr, perhaps more specifically. higher. Thanks again.

---

### Post by taurus on 2007-10-27
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by wyoming on 2007-10-28
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcfc3cfc3

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab92ab92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19173   154007091   83  Linux
/dev/sda2           19174       19929     6072570    5  Extended
/dev/sda5           19174       19929     6072538+  82  Linux swap / Solaris


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=026b42ff-8e1e-4ff7-9b07-b54f34df7ad0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d762d3c3-e3d7-4080-828c-4d47531a0d05 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sda1       /media/sda1     ntfs-3g defaults,locale=en_US.utf8 0    0

I have 2 physical HD, 250 GB and 80 GB. Unbuntu and what's left of XP+files on the largest. I don't know where these things are gone...

---

### Post by taurus on 2007-10-28
> **wyoming said:**
> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcfc3cfc3

   Device Boot      Start         End      Blocks   Id  System
**[COLOR="Blue"]/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS[/COLOR]**

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab92ab92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19173   154007091   83  Linux
/dev/sda2           19174       19929     6072570    5  Extended
/dev/sda5           19174       19929     6072538+  82  Linux swap / Solaris


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=026b42ff-8e1e-4ff7-9b07-b54f34df7ad0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d762d3c3-e3d7-4080-828c-4d47531a0d05 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
[B][COLOR="Red"]/dev/sda1       /media/sda1     ntfs-3g defaults,locale=en_US.utf8 0    0
[/COLOR][/B]
I have 2 physical HD, 250 GB and 80 GB. Unbuntu and what's left of XP+files on the largest. I don't know where these things are gone...

Right now, I only see one ntfs which is /dev/hda1.  So, you need to edit your /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace the red line with this new one.

```
dev/hda1       /media/hda1     ntfs-3g defaults,locale=en_US.utf8 0    0
```
Save it and then create a new mount point and mount it.

```
sudo mkdir /dev/hda1
sudo mount -a
df -h
```

---

### Post by wyoming on 2007-10-28
Thanks Taurus. In the mean time I got an answer from Maximus on another aspect of the same problem posted earlier (that's always how I get in trouble with puters: going too fast)
Now at boot I have the Ubuntu series and an option "XP 160 Gig".
When I choose that one, I now get XP boot menu with 3 options "FSX" (new name for my 80 Gig), "XP 160 Gigs" and "XP 80 Gigs".
FSX leads me to my 80 Gigs with XP on it. All OK.
XP 160 leads me to another hal.dll error
When I boot to FSX and check My Computer, there's only C:. The boot.ini repair I performed with the XP CD didn't give me any choice but C:: no other partition or HD available according to XP CD.
The only problem remaining is: can I access the XP partition on the partition where Ubuntu is? The remaining 90 Gigs (HD=250, partition =160) must be containing something. Or not. Again, I can live with that, but that would be perfect if I could retrieve a few things from my old XP.
Thanks again for your time!

---

### Post by taurus on 2007-10-28
If you don't have gparted, install it.  Then, fire it up (in System -> Administration) and see if it "sees" the rest of the space on your harddrive.

```
sudo apt-get update
sudo apt-get install gparted
```

---

### Post by wyoming on 2007-10-28
OK. GParted shows 2 devices:
- hda, 80 Gigs with an ntfs partition (XP) as hda1
- sda 153 Gigs with sda1 ext3 / as mount point and 147 Gigs in size, 6 Gigs used, boot; sda2, extended, 5.79 Gigs in size; sda5, linux-swap 5.79 Gigs in size.
There's still 100 Gigs missing... on the device sda..????

---

### Post by taurus on 2007-10-28
Can you post the screenshot of gparted and the output of this command from a terminal?

```
df -h
```

---

### Post by wyoming on 2007-10-28
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             145G  3.5G  134G   3% /
varrun               1014M  212K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   84K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   34M  980M   4% /lib/modules/2.6.22-14-generic/volatile

---

