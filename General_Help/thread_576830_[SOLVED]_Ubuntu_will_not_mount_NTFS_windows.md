---
title: "[SOLVED] Ubuntu will not mount NTFS windows"
date: 2007-10-15
forum: General Help
---

### Post by Fran89 on 2007-10-15
I had Festy t Fawn and it mounted and detected my windows partition beautifully, but upgrading to Gutsy Gibbon and i think messed up my partition table it says Partition 1 is not on cylinder boundary and refuses to mount my NTFS windows partition. Any help please  My windows Partition was not detected and had to be included manually, also it runs fine :confused: thanks in advanced

---

### Post by Fran89 on 2007-10-16
Please anyone, I really hate to *bump*

---

### Post by taurus on 2007-10-16
Post the output of these commands from a terminal.

```
sudo fdisk -l
cat /etc/fstab
```
What command do you use to mount it manually?

---

### Post by Fran89 on 2007-10-16
Yeah here it is..

```
root@Ubuntu:/home/francisco# sudo fdisk -l

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x794a368a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2996    24063448+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            2997        3648     5237190   83  Linux

root@Ubuntu:/home/francisco# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=bbb95d97-ea1b-42c3-b1f1-b708dd2c6905 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=466CA8F56CA8E143 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
root@Ubuntu:/home/francisco# 

```

I don't try to mount it manually, in festy it use to do it automatically in start up...  i did try to mount it manually tho using ntfs-3g command, no such luck

---

### Post by strabes on 2007-10-16
> i did try to mount it manually tho using ntfs-3g command, no such luck In gutsy you don't need to use the ntfs-3g filesystem type because it's included by default.

---

### Post by Fran89 on 2007-10-16
yeah so i thought  Festy also mounted it at start up, which its weird gutsy did not mount it, any ideas?

---

### Post by Fran89 on 2007-10-16
MY GOD this is the biggest blooper of all!!! i left windows in hibernation... I was starting up Ubuntu and out of the corner of my eye i see: NTFS in hibernation please remove so it can mount safely. even tho it happened fast i managed to see it, i entered windows shut it down ... and guess what... it mounted perfectly. I was like :lolflag: no freaking way  still thanks for your help. If any one can also help with this It wont make the intro noise at start up or shut down, It doesn't bother me tho sound is still good inside Ubuntu any how, so yeah... thanks

---

### Post by strabes on 2007-10-17
> **Fran89 said:**
> MY GOD this is the biggest blooper of all!!! i left windows in hibernation... I was starting up Ubuntu and out of the corner of my eye i see: NTFS in hibernation please remove so it can mount safely. even tho it happened fast i managed to see it, i entered windows shut it down ... and guess what... it mounted perfectly. I was like :lolflag: no freaking way  still thanks for your help. If any one can also help with this It wont make the intro noise at start up or shut down, It doesn't bother me tho sound is still good inside Ubuntu any how, so yeah... thanks

Glad to see you got it resolved. To disable the African-type sounds on login and logout, go to System > Preferences > Sound. Then go to the "sounds" tab. Then change "Log out" and "Log in" to "No sound." By the way, in the future you might want to be more clear with your questions, mostly things like using complete sentences. It makes it much easier for people to understand what you're talking about and help you.

Please mark this thread as resolved by clicking on "Thread Tools" at the top of the page.

---

### Post by Yoshiman007 on 2007-10-21
Just wanted to report that I had the same problem and after reading this realized that the last time i had booted windows, it had crashed out (go figure). After booting windows successfully, I shut down, and Gusty picked right back up on the Windows partition. Thanks for the help!

---

