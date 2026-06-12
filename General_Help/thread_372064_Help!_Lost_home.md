---
title: "Help! Lost /home"
date: 2007-02-27
forum: General Help
---

### Post by monstermudder78 on 2007-02-27
ok, so I followed these directions: [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome") to move my /home folder to a seperate partition, hda4.  I think I followed all the directions, but when I try and log in, I get an error, saying /home cannot be found.  So I used the live CD and followed the instructions at the bottom of the page to fix any problems, and of course, the problem is still there.  So my question is either how do I undo what I did, or how do I just make it work the way it is supposed to?  If I left out anything you need to know, please ask, I get in the most trouble when I have to keep reinstalling the whole thing :) .

---

### Post by taurus on 2007-02-27
From the LiveCD, mount / and post your /etc/fstab here.

```
sudo fdisk -l
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
cat /mnt/ubuntu/etc/fstab
```
Assuming /dev/hda1 is where / is located.

---

### Post by monstermudder78 on 2007-02-27
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            4458        7349    23229990   83  Linux
/dev/hda3            7350        7476     1020127+   5  Extended
/dev/hda4            1913        4457    20442712+  83  Linux
/dev/hda5            7350        7476     1020096   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda2 /mnt/ubuntu
ubuntu@ubuntu:~$ cat /mnt/ubuntu/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
ubuntu@ubuntu:~$

```

---

### Post by taurus on 2007-02-27
Well, you never mount /dev/hda4 to /home so that's where the problem is.  From the LiveCD (while /dev/hda2 is still being mounted), edit /mnt/ubunt/etc/fstab

```
gksudo gedit /mnt/ubuntu/etc/fstab
```
and add this line to the end of it.

```
/dev/hda4   /home   ext3   defaults   0   1
```
Save it.  Unmount your / and reboot.

```
sudo umount /dev/hda2
```

---

### Post by monstermudder78 on 2007-02-27
Hey thanks a million!  It is working now, I really appreciate ur help.

---

### Post by taurus on 2007-02-27
You're welcome and have fun.

---

