---
title: "change home folder path to..."
date: 2007-06-03
forum: General Help
---

### Post by andreasmascher on 2007-06-03
Hi there!

I reinstalled ubuntu. Before I did this, I used this tutorial to change physically the position of my home folder to another drive: 

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

It worked pretty good but no on my new installed OS I cant figure out how to change the position again. Weird, I know. 

Here's the problem: 
How do I find out what the name of my drive is, gpart doesn't work. I installed it using apt-get install but when I type in the terminal it just shows 

> andi@derandi:~$ gpart
Usage: gpart [options] device
Options: [-b <backup MBR>][-C c,h,s][-c][-d][-E][-e][-f][-g][-h][-i]
         [-K <last sector>][-k <# of sectors>][-L][-l <log file>]
         [-n <increment>][-q][-s <sector-size>][-t <module-name>]
         [-V][-v][-W <device>][-w <module-name,weight>]
gpart v0.1h (c) 1999-2001 Michail Brzitwa <michail@brzitwa.de>.
Guess PC-type hard disk partitions.


What I need to do is just changing the path to my new hard drive home folder. Can't be that hard, ey?

Ah, by the way It should mount the drive when I start the computer. 

Easy for ya ain't it?? :)

---

### Post by dbott67 on 2007-06-03
To get a listing of partitions, you can use 'sudo fdisk -l'.

Can you post the output of the following commands:
```
dbott@feisty:~$ [COLOR=Red]**sudo fdisk -l**[/COLOR]
Password:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1912    15358108+  83  Linux
/dev/sda2            1913        4462    20482875   83  Linux  [COLOR=Purple]*<-- my /home partition*[/COLOR]
/dev/sda3            4463        4865     3237097+  82  Linux swap / Solaris

```
My fstab file *(used to mount partitions at boot time)*
```
dbott@feisty:~$ [COLOR=Red]**cat /etc/fstab**[/COLOR]
# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7366345e-067b-44b6-ab33-c8af8c31ae86 /               ext3    defaults,errors=remount-ro 0       1
[COLOR=Red]# /dev/sda2 - /home partition[/COLOR]
[COLOR=Red]UUID=d98db2a6-db44-4405-bbb1-4bb5f1cb8faa /home           ext3    defaults        0       2[/COLOR]
# /dev/sda3
UUID=4c5a5618-2d15-441f-b847-3b1b0d796a82 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

//192.168.1.2/Music /home/dbott/music   smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
//192.168.1.2/Data /home/dbott/data   smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
//192.168.1.2/Archive /home/dbott/archive1 smbfs auto,credentials=/root/.credentials,uid=1000,umask=000,user 0 0

```
And finally, post all mounted partitions:
```
dbott@feisty:~$ [COLOR=Red]**mount**[/COLOR]
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
[COLOR=Red]/dev/sda2 on /home type ext3 (rw)[/COLOR]  [COLOR=Purple]*#<-- here's my /home partition*[/COLOR]
//192.168.1.2/Music on /home/dbott/music type smbfs (rw)
//192.168.1.2/Data on /home/dbott/data type smbfs (rw)
//192.168.1.2/Archive on /home/dbott/archive1 type smbfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

-Dave

---

### Post by andreasmascher on 2007-06-05
Thx for the first step, hope you'll help me out here!

Looks like a little chaos actually, but has its reasons! The drive with my actual home folder is the big one with 160GB. Must be hdc5... right?



> Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5006    40210663+  83  Linux
/dev/hda2            5007       10010    40194630    f  W95 Ext'd (LBA)

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9553    76734441   83  Linux
/dev/hdb2            9554        9964     3301357+   5  Extended
/dev/hdb5            9554        9964     3301326   82  Linux swap / Solaris

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc2               2       19457   156280320    f  W95 Ext'd (LBA)
/dev/hdc5               2       19457   156280288+  83  Linux
andi@derandi:~$ 


okay, let's see what fstab has to offer: 

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=e39fe4e2-0d80-4966-9553-9e3eb8bc60db /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=ba09c403-9408-407b-8a00-59aedee133d0 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0


To me it looks like the drive is mounted but not by default when I boot? Might be because I am usually accessing it using "Places - Disk" and it'll be mounted kind of on request. 

:popcorn:

Okay, it's fun. 

> andi@derandi:~$ mount
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdd on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=andi)


mmm, can't find it here though. 

**How can I set the home folder?** :p

mm, you may wonder why I don't use the tutorial again right? It does some stuff I don't really understand and I am afraid loosing my data! I don't care about the default home folder I am using in the mean time. But overwriting the one on my 160 GB drive would be... you know I would burst into tears!

---

### Post by andreasmascher on 2007-06-05
does anybody know what to do next?

---

