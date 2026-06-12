---
title: "Help Mounting USB DEvice Please"
date: 2013-01-06
forum: General Help
---

### Post by Quarkrad on 2013-01-06
I can 'play' with my ipod Touch device when I'm using virtualbox, under Devices/USB it is seen and easily connected.  However, in my native 12.04 OS it is not seen when connected to a usb port.  lsusb shows that it is there:

**Bus 002 Device 005: ID 05ac:1293 Apple, Inc. iPod Touch 2.Gen**


What can I do so that when ever I connect this device 12.04 always mounts it - like a random connection of a usb memery stick is always mounted?   Thanks.

---

### Post by Quarkrad on 2013-01-06
Interestingly when I launch Clementine (music player) it sees my ipod and list the songs.  Although I believe it does not have the functionality to take tracks off the ipod or put them on.  Whereas, I beleive, gtkipod can.  So nautilus does not see my ipod, or gtkipod but Clementine does.

---

### Post by sudodus on 2013-01-06
> **Quarkrad said:**
> Interestingly when I launch Clementine (music player) it sees my ipod and list the songs.  Although I believe it does not have the functionality to take tracks off the ipod or put them on.  Whereas, I beleive, gtkipod can.  So nautilus does not see my ipod, or gtkipod but Clementine does.
What can these terminal commands see:

```
sudo fdisk -lu
```
```
sudo blkid
```

If seen by them, the ipod might be possible to mount by ***mount*** with or without an entry in [FONT="Courier New"][SIZE="3"]/etc/fstab[/SIZE][/FONT].

*Edit*: Or check with ```
df
``` when playing songs from it with Clementine

---

### Post by Us3r Unfriendly on 2013-01-06
ifuse /path/to/mount --root
have idevice plugged in

sudo umount /path/to/mount
when you want to unmount it :D

---

### Post by Quarkrad on 2013-01-06
I could not see the ipod device using your commands (for fstab) although df gave me:

[B]dad@dadubuntu:~$ df
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda2      100791728  21554992  74116736  23% /
udev             1973712         8   1973704   1% /dev
tmpfs             793008       872    792136   1% /run
none                5120         0      5120   0% /run/lock
none             1982516        88   1982428   1% /run/shm
/dev/sda3      275393532 229899048  45494484  84% /media/store
/dev/sda1      102398972  47974480  54424492  47% /media/winXP
/dev/sdb5      976759804 301357484 675402320  31% /media/backup[/B]

as a newbie I recognise most but not sure what the none items are - /run/lock, run/shm

---

### Post by Quarkrad on 2013-01-06
Not sure what I can do with ifuse /path/to/mount --root  - I assume this commands follows from the previous post - i.e. I know the path of the device (which I do not).

---

### Post by sudodus on 2013-01-06
> **Quarkrad said:**
> I could not see the ipod device using your commands (for fstab) although df gave me:

Did you find anything that might be the ipod with any of the commands fdisk and blkid from my previous post?

*Edit*: if you are not sure, post the output of those two commands
> 


```
dad@dadubuntu:~$ df
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda2      100791728  21554992  74116736  23% /
udev             1973712         8   1973704   1% /dev
tmpfs             793008       872    792136   1% /run
none                5120         0      5120   0% /run/lock
none             1982516        88   1982428   1% /run/shm
/dev/sda3      275393532 229899048  45494484  84% /media/store
/dev/sda1      102398972  47974480  54424492  47% /media/winXP
/dev/sdb5      976759804 301357484 675402320  31% /media/backup
```

as a newbie I recognise most but not sure what the none items are - /run/lock, run/shm
/run/lock, run/shm belong to the system and have nothing to do with an attached USB device. /media/backup seems to be a 1 GB backup partition on a separate drive.

When you play music from it with Clementine, it should be mounted or something similar to mounted at least. Could it be recognized as a CDROM? Check at the root:

```
cd /
```
```
ls -l
```

or with Nautilus

Check for /cdrom or similar or /sr0

---

### Post by Quarkrad on 2013-01-06
I launched Clemetine and played a song - this is the output of the terminal command (attached).

---

### Post by sudodus on 2013-01-06
> **Quarkrad said:**
> I launched Clemetine and played a song - this is the output of the terminal command (attached).
OK, 

1. What do you see in the /cdrom directory? You can use Nautilus or the terminal window.

2. You can also post the output of the following commands while Clementine is playing

```
sudo fdisk -lu
```
```
sudo blkid
```
```
cat /etc/mtab
```
It is simpler to cut and paste from the terminal window than to make a screen dump and attach it as a picture:

Mark the text, and then copy it to clipboard with
***Edit - Copy*** (pull down menu items)

And paste it into 'this editing window of Ubuntu Forums'. Finally surround it with code tags

[noparse]```
output
```[/noparse]
 
to get output like this
 
```
output
```

---

### Post by Quarkrad on 2013-01-06
Thanks for the 'how to' - wondered how to do this for a time.

Here are the outputs whilst playing a song.

```
dad@dadubuntu:~$ sudo fdisk -lu
[sudo] password for dad: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfa0c1e50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   204799999   102398976    7  HPFS/NTFS/exFAT
/dev/sda2       204802048   409602047   102400000   83  Linux
/dev/sda3       409602048   960389119   275393536    7  HPFS/NTFS/exFAT
/dev/sda4       960391166   976773119     8190977   85  Linux extended
/dev/sda5       960391168   976773119     8190976   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x638c197f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1953523711   976760832    5  Extended
/dev/sdb5            4096  1953523711   976759808    7  HPFS/NTFS/exFAT
dad@dadubuntu:~$
```


```
dad@dadubuntu:~$ sudo blkid
[sudo] password for dad: 
/dev/sda1: LABEL="winXP" UUID="AE905F64905F3257" TYPE="ntfs" 
/dev/sda2: UUID="903756de-cfba-405e-8d1d-c91fa9afc192" TYPE="ext4" 
/dev/sda3: LABEL="store" UUID="09D6A06006C8DACD" TYPE="ntfs" 
/dev/sda5: UUID="9d21cf3a-d202-4f59-9cb7-497b390f52fb" TYPE="swap" 
/dev/sdb5: LABEL="backup" UUID="53E871870E731F3D" TYPE="ntfs" 
dad@dadubuntu:~$ 
```

```
dad@dadubuntu:~$ cat /etc/mtab
/dev/sda2 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda3 /media/store fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sda1 /media/winXP fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sdb5 /media/backup fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
rpc_pipefs /run/rpc_pipefs rpc_pipefs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
gvfs-fuse-daemon /home/dad/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=dad 0 0
dad@dadubuntu:~$ 
```

---

### Post by Quarkrad on 2013-01-06
The sda s are my partitions on HD1 and sdb is my backup partition on HD2.

---

### Post by sudodus on 2013-01-06
> **Quarkrad said:**
> Thanks for the 'how to' - wondered how to do this for a time.

Here are the outputs whilst playing a song.
...
```

rpc_pipefs /run/rpc_pipefs rpc_pipefs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0

```
I don't recognize these two lines (from my mtab). Maybe they contain something? Try and look at the following directories

```
/run/rpc_pipefs
```
and 
```
/proc/fs/nfsd
```
Maybe they contain what you are looking for. I have more hope for the first one, the other one might be related to an NFS service, that you are running. But look at both...

---

### Post by Quarkrad on 2013-01-06
Two more pictures I'm afraid.  Pic1 shows a number of folders within rpc_pipefs - they are all empty - even with Show Hidden Files turned on. Pic2 shows the content of nfsd.

---

### Post by sudodus on 2013-01-06
> **Quarkrad said:**
> Two more pictures I'm afraid.  Pic1 shows a number of folders within rpc_pipefs - they are all empty - even with Show Hidden Files turned on. Pic2 shows the content of nfsd.
No luck with that. I don't know how it is connected. Probably several people at the Ubuntu Forums know. Let us hope that at least one of them will read your thread :-)

By the way: did you check /cdrom (and whatever it is linked to)?

---

### Post by Quarkrad on 2013-01-06
Clementine is playing - there is nothing in /cdrom.  I guess we have reached the end of the road.  I installed Amarok, which is what Clementine was based on and it too sees the ipod.  Anyway, thanks for all your help - I appreciate the time you have spent on this.

---

### Post by Us3r Unfriendly on 2013-01-07
I guess what your trying to do is connect your idevice to your Ubuntu machine, correct?  Your going to have to mount it first by issueing the following commands:

mkdir ~/iDeviceMount/

ifuse ~/iDeviceMount/ --root

cd ~/iDeviceMount/; ls -A ./

...this allows you to mount your iDevice in a folder that is created in your home directory as example and allows you to enter that directory and list all in the directory.

---

### Post by Quarkrad on 2013-01-07
Thanks.  It looks using this method I have to jailbreak my device.  Is there a way of mounting/using gtkpod without jailbreaking?  Clementine and Amarok can read the device as it is.

---

