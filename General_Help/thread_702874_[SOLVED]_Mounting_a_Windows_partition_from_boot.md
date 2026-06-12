---
title: "[SOLVED] Mounting a Windows partition from boot"
date: 2008-02-20
forum: General Help
---

### Post by Cilionelle on 2008-02-20
Can someone please walk me through or point me to setting up my Windows partition to mount at boot, rather than manually through Places > Computer > 49.9GB drive.  I'd like my wife's experience of Ubuntu to be as easy as possible, and, having only ever had a full install (leaving Windows behind, something I can't do at the moment), I have never had experience of this.

There were a few options found by the "Here are the similar threads we found" bitty, but all were relatively old (I don't know if switching to 7.10 has changed stuff that much, but I'd prefer a fresh approach).  And it seems I can write to the Windows partition quite fine, which was ruled out by many of the previous threads.

Cheers!

---

### Post by sisco311 on 2008-02-20
please post the output from:

```
mount
```

```
sudo fdisk -l
```

```
cat /etc/fstab
```

---

### Post by jken146 on 2008-02-20
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Yellow Pasque on 2008-02-20
One you have the /dev path for the partition you want to mount, then add this to fstab:
```
/dev/<device name, partition number>  /<dir you want to mount to>   ntfs-3g  rw,auto,exec,user,uid=1000  0  0
```

---

### Post by Cilionelle on 2008-02-20
Output from the commands from sisco311:

```
tom@satris:~$ mount 
/dev/sda3 on / type ext3 (rw,errors=remount-ro) 
proc on /proc type proc (rw,noexec,nosuid,nodev) 
/sys on /sys type sysfs (rw,noexec,nosuid,nodev) 
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755) 
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777) 
udev on /dev type tmpfs (rw,mode=0755) 
devshm on /dev/shm type tmpfs (rw) 
devpts on /dev/pts type devpts (rw,gid=5,mode=620) 
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw) 
securityfs on /sys/kernel/security type securityfs (rw) 
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=tom) 
/dev/sda2 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096) 
tom@satris:~$ sudo fdisk -l 
[sudo] password for tom: 

Disk /dev/sda: 80.0 GB, 80000000000 bytes 
255 heads, 63 sectors/track, 9726 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xd0f4738c 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1           4       32098+  de  Dell Utility 
/dev/sda2   *           5        6514    52291575    7  HPFS/NTFS 
/dev/sda3            6515        9587    24683872+  83  Linux 
/dev/sda4            9588        9726     1116517+   5  Extended 
/dev/sda5            9588        9726     1116486   82  Linux swap / Solaris 
tom@satris:~$ cat /etc/fstab 
# /etc/fstab: static file system information. 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
# /dev/sda3 
UUID=9321a1a5-2dd8-40f3-9135-02573f03467b /               ext3    defaults,errors=remount-ro 0       1 
# /dev/sda5 
UUID=2578ee54-66f8-4a18-b8f4-bfc8ebb6114a none            swap    sw              0       0 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0 
```

I followed the psychocat's guide, but the file /etc/fstab looks a lot different to the examples listed, and sda2 is not even listed in the file.

Temüjin, how do I find out the /dev path?  And do I need to create a dir for it to mount too, or just use an existing one?

Cheers!

---

### Post by Yellow Pasque on 2008-02-20
The path is /dev/sda2 as you can see from the fdisk output.

You can mount to whatever empty directory you'd like, for example, /media/disk:
```
/dev/sda2  /media/disk   ntfs-3g  rw,auto,exec,user,uid=1000  0  0
```

---

### Post by Cilionelle on 2008-02-20
> **Temüjin said:**
> The path is /dev/sda2 as you can see from the fdisk output.

Of course... silly me.

> **Temüjin said:**
> You can mount to whatever empty directory you'd like, for example, /media/disk:
```
/dev/sda2  /media/disk   ntfs-3g  rw,auto,exec,user,uid=1000  0  0
```

Thanks.  Is it possible to simply copy that code into the /etc/fstab file, save it and reboot?

---

### Post by Yellow Pasque on 2008-02-20
> Thanks. Is it possible to simply copy that code into the /etc/fstab file, save it and reboot?

Yes, but make sure /media/disk exists first with this command:
```
file /media/disk
```
should return: /media/disk: directory

If it says: /media/disk: cannot open `/media/disk' (No such file or directory), then:
```
cd /media
sudo mkdir disk
sudo chmod 777 disk
```

---

### Post by sisco311 on 2008-02-20
and don't reboot. save the file and:
```
sudo mount -a
```
and see if the partition is mounted

---

### Post by Cilionelle on 2008-02-20
Thanks to all who helped out!  Problem solved... now to get the internet working on it!

---

### Post by jldeshpande on 2008-02-25
> **sisco311 said:**
> please post the output from:

```
mount
```

```
sudo fdisk -l
```

```
cat /etc/fstab
```
--------------------------------------------------

Wil you kindly help me too?
Since long i have kept sda5 & sda6 as FAT32 to try & switch over to linux.
Soon after getting broadband , duel booted ubuntu studio  before 2 weeks,but have to mount them  always.How to automount them at boot?
Giving details
-------------------------------
1]mount

j@ubuntu:~$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-rt/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda8 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda5 on /media/disk-1 type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
/dev/sda6 on /media/disk-2 type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
/dev/sdb7 on /media/OSBkup type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
j@ubuntu:~$ 



2]]sudo fdisk -l


j@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d081d07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3920    31487368+   7  HPFS/NTFS
/dev/sda2            3921       19457   124800952+   f  W95 Ext'd (LBA)
/dev/sda5            3921        7975    32571756    b  W95 FAT32
/dev/sda6            7976       12156    33583851    b  W95 FAT32
/dev/sda7           12157       16465    34612011    7  HPFS/NTFS
/dev/sda8           16466       19457    24033208+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf3f3f3f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       17448       19457    16145325   83  Linux
/dev/sdb2               2       17447   140134995    f  W95 Ext'd (LBA)
/dev/sdb5               2        6541    52532518+   7  HPFS/NTFS
/dev/sdb6            6542       11105    36660298+   7  HPFS/NTFS
/dev/sdb7           11106       17353    50187028+   7  HPFS/NTFS
/dev/sdb8           17354       17447      755023+  82  Linux swap / Solaris

Partition table entries are not in disk order
j@ubuntu:~$ 
-----------------------------------


3] cat /etc/fstab


j@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sdb1
UUID=710ab0af-d1a1-4d67-8bce-ca593aad369e / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sdb8
UUID=37336730-75be-43b5-a27d-c378da0f3887 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
j@ubuntu:~$ 

------------------------------
I am new to command line.
Through kubuntu GUI automounted sda5 & sda6,but reverted as it was read only.I need rw.
What is to be done for other NTFS partitions?

Is not there any easy way without terminal usage? I mean--by right clicking the partition in 'my computer',selecting  'properties'. and under  'volume'tab giving settings? What settings,especially  regarding mount option should i give so that it will mount at boot as read & write? 

I am getting exhausted in searching and learning new things. 

Thanking in anticipation.

  J.L.Deshpande

---

### Post by sisco311 on 2008-02-25
> [jldeshpande]("http://ubuntuforums.org/member.php?u=498722")fat32:

please post the output of:
```
ls -all /media/
```ntfs:
to mount a partition: 
1.)create a mount point(a directory).
```
sudo mkdir /media/**<name of your partition here>**
```replace** <name of your partition here> ** with whatever you want.: exemple: windows, music, movie, data or sdaX

You need different mount points for the partitions.

2.) edit your fstab:
```
sudo kate /etc/fstab
```in gnome replace kate with gedit.
add this line> /dev/**<partition id> **/media/**<name of your partition here> **[SIZE=3]ntfs    defaults,umask=007,gid=46 0       1[/SIZE]replace **<partition id> **with one of your ntfs partitions: sda1, sda7, sda8, sdb5, sdb6 or sdb7

3.)To get read/write permission change the owner of the directory:
```

sudo chown -R root:plugdev /media/**<name of your partition here>**
```Add your user to plugdev group:
```
sudo usermod -a -G plugdev <username>
```replace <username> with your user name.

mount your partition:
```
sudo mount -a
```

open your file browser an d check if your partition is mounted at /media/<name of your partition>

---

### Post by jldeshpande on 2008-02-26
sisco311  -- pl
I am unable to boot in ubuntu! May be it's my mistake.This i am typing thro' windows.
To have default gdm,i changed kdm to gdm in etc/x11/default-display-manager/user/bin ,after reading in forum.[I am not blaming forum!Because of this forum only i could try ubuntu,otherwise anybody would have left it soon.]    This i was tempted to do because,after installing KDE on ubuntu studio 7.10,i observed that it has become a mesh now,many of gnome options like login screen etc. have disappeared.Moreover,as mentioned earlier,in kubuntu i was not able to mount partition as rw,always required to log in to gnome to mount partitions.Hence wanted to have gnome as default.For that i entered code  'gksudo nautilus'  through ubuntu gnome,opened x11 /default-display-manager,changed kdm to gdm,saved. But some error message was displayed, may be regarding authentication.[It seems,i was no more a owner in gnome after installing KDE.]to check what has happened  i restarted.By default it took the ubuntu kernal,displayed kubuntu logo with progress bar & thereafter letters on black screen saying something like 'image missing or not found'.Here my user name and password was accepted,but what to do next?
I rebooter and entered recovery mode.There it says x11 is a directory,default-display-manager is a directory.But how to revet gdm to kdm?
I am sorry i dont know about command line operations,hence giving trouble to you people.
Will anybody pl help me in getting back the lost paradise,the killing default ubuntu studio 7.10 grey theme?
After that only i can try mounting partitions as advised by you.
Thanking in anticipation.

---

### Post by sisco311 on 2008-02-26
you can use nano to edit the file:
```
sudo nano /etc/X11/default-display-manager
```> /usr/sbin/kdmCtrl+o, Enter to save and Ctrl+x to exit

start the gui:
```
startx
```or you can start kde:

```
sudo kdm
```

---

### Post by jldeshpande on 2008-02-27
> **sisco311 said:**
> you can use nano to edit the file:
```
sudo nano /etc/X11/default-display-manager
```Ctrl+o, Enter to save and Ctrl+x to exit

start the gui:
```
startx
```or you can start kde:

```
sudo kdm
```
----------------------------------------------------------------------------------


Hi sisco311
```
sudo kdm
```
worked & I got a lot of relief after seeing my favorite grey theme after a long time.
Thanks a lot!
Thereafter i tried to edit 'default-display-manager'.
The things didn't take place exactly as mentioned by you,may be some fault on my side,but after trying for an hour finally 'gdm' got changed to' kdm'.Now i need not enter 'sudo kdm' after logging in.
I think i will have to carry on with this kdm only.
I am too much relieved now.
Thanks once again.:-({|=

---

### Post by jldeshpande on 2008-02-27
> **sisco311 said:**
> fat32:

please post the output of:
```
ls -all /media/
```
>
--------------------------------------------------------
Giving the details you asked for

j@ubuntu:~$ ls -all /media/
total 24
drwxr-xr-x  6 root root 4096 2008-02-27 23:38 .
drwxr-xr-x 22 root root 4096 2008-02-20 21:35 ..
lrwxrwxrwx  1 root root    6 2008-02-03 23:28 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-02-03 23:28 cdrom0
drwxr-xr-x  2 root root 4096 2008-02-20 21:53 d
drwxr-xr-x  2 root root 4096 2008-02-20 21:44 D
lrwxrwxrwx  1 root root   45 2008-02-20 10:09 .directory -> /etc/kubuntu-default-settings/directory-media
drwxr-xr-x  2 root root 4096 2008-02-20 21:43 E
-rw-r--r--  1 root root    0 2008-02-27 23:38 .hal-mtab
lrwxrwxrwx  1 root root   42 2008-02-20 10:09 .hidden -> /etc/kubuntu-default-settings/hidden-media
j@ubuntu:~$ 
------------------------

Before an hour booted in Ubuntu successfully with your guidance.
This is not less for today. I will relax & rejoice  at least for a day now.Who knows again what wrong i will do in auto mounting the Partitions?....LOL
Meanwhile submitting the above details & preparing myself mentally for the next lesson.
This forum is really great!---i mean  you people too!!!because of whom this forum is!

---

### Post by sisco311 on 2008-02-28
just create two mount points for your fat partitions:
```
sudo mkdir /media/sda5
sudo mkdir /media/sda6

```and add this lines to your /etc/fstab(kdesudo kate /etc/fstab):
> /dev/sda5       /media/sda5 vfat iocharset=utf8,umask=000 0 0
/dev/sda6       /media/sda6 vfat iocharset=utf8,umask=000 0 0and remount the partitions:
```
sudo umount /dev/sda5
sudo umount /dev/sda6
sudo mount -a
```

---

