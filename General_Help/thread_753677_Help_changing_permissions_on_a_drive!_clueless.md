---
title: "Help changing permissions on a drive! clueless"
date: 2008-04-13
forum: General Help
---

### Post by McTwist724 on 2008-04-13
Hey! I just recently switched from XP to Ubuntu and man, I'm lovin it so far! But I'm still having one problem, that is changing the permission of the drive/volume from root to the user. I can read, but cannot write. I've tried a whole bunch of commands in terminal, such as the sudo chown -r 'drive name', etc, etc. None of it worked.

I am running Ubuntu 7.10 and the secondary HDD I have is an NTFS partition which is under the control of 'root'. I would like to be able to change the permission from root to the user (cman) so I can edit my music collection and change the ID3 tags without having to use a program. I could use Amarok to edit the tags but I'd rather do it without the assistance of a program. I can still copy, move, delete, and rename files, but I cannot edit them, as in the ID3 tags. 

Any help on the matter would be greatly appreciated

thanks

peace

---

### Post by SorryGoFish on 2008-04-13
chown -R <username> <mountpoint>
chmod u+w <mountpoint>

Where mountpoint in like /media/drive . The first command makes it yours (recursively with -R). And the second line makes sure the user (u) has write permissions.

---

### Post by McTwist724 on 2008-04-13
Wow, thanks for the quick reply.

It still seems, even after I correctly entered the commands in terminal, that the drive permissions are still controlled by root.

Any other suggestions?

oh and I do I need to have the < > around my user and mount point do I?

---

### Post by jocko on 2008-04-13
> **McTwist724 said:**
> oh and I do I need to have the < > around my user and mount point do I?
No.

It could be that the drive is not mounted with user read-write permission.
Could you post the contents of your /etc/fstab?
```
cat /etc/fstab
```

---

### Post by McTwist724 on 2008-04-13
Ok, here are the results:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6be1d9fc-fd01-46d3-bb4d-d5d94e9b79af /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8c12f829-c766-48e3-81c5-ef52167b1984 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by McTwist724 on 2008-04-13
anyone??

---

### Post by jocko on 2008-04-14
Your ntfs drive is not in fstab. Do you mount it manually? How?
What's the output of:```
sudo fdisk -l
```and:```
 ls -l /dev/disk/by-uuid/
```?

---

### Post by McTwist724 on 2008-04-14
Umm, it's already mounted when I log on and off so idk.

sudo fdisk -l results:

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2527a2c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9324    74894998+  83  Linux
/dev/sda2            9325        9726     3229065    5  Extended
/dev/sda5            9325        9726     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x095030ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       33848   271884028+   7  HPFS/NTFS
/dev/sdb2           33849       48641   118824772+   7  HPFS/NTFS



 ls -l /dev/disk/by-uuid/ results:

total 0
lrwxrwxrwx 1 root root 10 2008-04-12 14:43 12501A46501A3149 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2008-04-12 14:43 2C641A256419F1F6 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-04-12 14:43 6be1d9fc-fd01-46d3-bb4d-d5d94e9b79af -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-04-12 14:43 8c12f829-c766-48e3-81c5-ef52167b1984 -> ../../sda5


here they are, sorry i am not of much help

---

### Post by jocko on 2008-04-14
> **McTwist724 said:**
> Umm, it's already mounted when I log on and off so idk.
That's weird. I was sure a partition must be listed in fstab in order to be mounted automatically... So I guess it's mounted in some other way, that I'm not aware of, but I will try to help you to get it working through fstab.

So you have two ntfs partitions, /dev/sdb1 and /dev/sdb2:
```
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       33848   271884028+   7  HPFS/NTFS
[COLOR=Red][COLOR=Blue] /dev/sdb2[/COLOR]       [/COLOR][COLOR=black]33849       48641   118824772+   7  HPFS/NTFS[/COLOR]
```I guess you have windows on the first one, and the second one is a data partition that you need write permissions to?
You need to know the uuid (some kind of unique identification code) for the partition you want to mount, that's revealed by the output of the 'ls -l' you provided:
```
[COLOR=Red][COLOR=black]lrwxrwxrwx 1 root root 10 2008-04-12 14:43 [/COLOR]12501A46501A3149[COLOR=black] -> ../../[/COLOR][/COLOR][COLOR=Blue]sdb2[/COLOR]
lrwxrwxrwx 1 root root 10 2008-04-12 14:43 2C641A256419F1F6 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-04-12 14:43 6be1d9fc-fd01-46d3-bb4d-d5d94e9b79af -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-04-12 14:43 8c12f829-c766-48e3-81c5-ef52167b1984 -> ../../sda5
```What you need to do is this:
```
sudo mkdir [COLOR=Blue]/media/sdb2[/COLOR]
gksudo gedit /etc/fstab
```Add this to the end of the file:
```
# Entry for [COLOR=Blue]/dev/sdb2[/COLOR] :
UUID=[COLOR=Red]12501A46501A3149[/COLOR] [COLOR=Blue]/media/sdb2[/COLOR] ntfs defaults,umask=007,gid=46 0 1
```Note that you can change the "[COLOR=Blue]sdb2[/COLOR]" in  "[COLOR=Blue]/media/sdb2[/COLOR]" to whatever you like the mount point to be called, and if you don't want the disk to appear on your desktop, use "[COLOR=Blue]/mnt/[/COLOR]" instead of "[COLOR=Blue]/media/[/COLOR]".


And finally, make sure you have the package "ntfs-3g" installed (that's the ntfs driver):
```
 sudo apt-get install ntfs-3g
```

And re-mount the partition with this command:
```
sudo umount /dev/sdb2
sudo mount -a
```

---

### Post by chaime on 2008-04-14
ok...I still don't understand what the added parameters in the fstab file (above) mean.

i am trying to mount an ext3 filesystem as myself (chaime) that has only root permissions. I want to use this as my storage drive, but it won't let me write. it is sdb1 according to Linux, and its UUID is contained in the following line: 

UUID=9bae4dc3-cdd4-4fc0-b317-cf5557fbbdae /media/sdb1     ext3    defaults        0       2

...also, is there ANY way to actually NAME the drives so that I don't always have to think oh yeah, sdb, that's my second physical drive, and 1, is the partition that debian recognizes first, so yeah sdb1 must be my storage drive...etc.??

Thanxxxxxx

Chaim

---

### Post by jocko on 2008-04-15
> **chaime said:**
> ok...I still don't understand what the added parameters in the fstab file (above) mean.

i am trying to mount an ext3 filesystem as myself (chaime) that has only root permissions. I want to use this as my storage drive, but it won't let me write. it is sdb1 according to Linux, and its UUID is contained in the following line: 

UUID=9bae4dc3-cdd4-4fc0-b317-cf5557fbbdae [COLOR=Blue]/media/sdb1[/COLOR]     ext3    defaults        0       2

...also, is there ANY way to actually NAME the drives so that I don't always have to think oh yeah, sdb, that's my second physical drive, and 1, is the partition that debian recognizes first, so yeah sdb1 must be my storage drive...etc.??

Thanxxxxxx

Chaim

That fstab line looks exactly like mine (for my ext3 file systems that I have complete access to), that means you should be able to change the owner of the entire partition by:
```
sudo chown -R [COLOR=Red]username:groupname[/COLOR] /media/sdb1
``` (if your username is chaime, so is your groupname, so that would be chaime:chaime).
Note: Never use this command on the root of your file system or any of the system directories on the root file system.

by naming the drive I guess you mean that you want it to be /media/storage or something other than /media/sdb1?
In that case, first make a new mount point with the name you want:
```
sudo mkdir /media/storage
```Then edit your fstab to use the new mount point:```

gksudo gedit /etc/fstab
``` Find the line that specifies the mount point for the partition you wish to rename and change it so that it points to the new mount point (in this example, change the line in your last post from /media/sdb1 to /media/storage, but don't change anything else).
Then to remount the partition in the new place:
```
sudo umount /dev/sdb1
sudo mount -a
```After it has been remounted to the new place, you can (but you don't need to) remove the old mount point (first make sure nothing is mounted in it. It should appear as an empty folder if you browse to it). ```
sudo rmdir /media/sdb1
```

---

### Post by noswal on 2008-04-15
FWIW I wanted to access files of F: my other windows drive which is sda1 in unbuntu. I just added it as a line in fstab and can now access it after reboot.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda6       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
# Entry for /dev/sda1 :
/dev/sda1       /media/sda1 ntfs         defaults,nls=utf8,umask=007,gid=46 0 1

---

