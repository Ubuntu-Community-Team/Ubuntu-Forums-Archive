---
title: "[SOLVED] Filesystem Full"
date: 2008-05-11
forum: General Help
---

### Post by SnakeHips on 2008-05-11
I've got a problem thats driving me nuts. I have a 11Gig partition /dev/sda2 that contains my / partition and around 10Gigs is showing as used

```
[root@desk /]# df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             11061600   9950416    661688  94% /
none                    513480         0    513480   0% /dev/shm
/dev/sda1                31077      9036     20437  31% /boot
/dev/sda3             30857272   7735864  21867376  27% /home
/dev/sda6             50795348   5885408  42349984  13% /mnt/data

```
I'm expecting to see around 2Gigs used for the filesystem and this is confirmed with...

```
[root@desk /]# du -hsx
2.2G
```

Apps/system tools/Disk usage analyser reports the same.

So ,I'm missing something like 8Gigs of free space and cant find it!

```
[root@desk /]# du -s * | sort -n
0	proc
0	sys
4	lib64
4	srv
16	lost+found
16	media
44	tmp
384	dev
388	root
5160	bin
8660	boot
13360	sbin
38864	opt
54480	etc
75316	var
84432	lib
1939152	usr
5701172	mnt
7559688	home
```

```
[root@desk /]# dumpe2fs -h /dev/sda2
dumpe2fs 1.40.8 (13-Mar-2008)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          1a172ce3-6f7e-48f5-a53e-fe65220004c7
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              1400768
Block count:              2809366
Reserved block count:     112374
Free blocks:              277796
Free inodes:              1282129
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      619
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16288
Inode blocks per group:   509
Filesystem created:       Mon May  5 19:47:35 2008
Last mount time:          Sun May 11 13:18:29 2008
Last write time:          Sun May 11 13:18:29 2008
Mount count:              13
Maximum mount count:      33
Last checked:             Sat May 10 18:19:07 2008
Check interval:           15552000 (6 months)
Next check after:         Thu Nov  6 17:19:07 2008
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:		  128
Journal inode:            8
First orphan inode:       1160305
Default directory hash:   tea
Directory Hash Seed:      6839bf90-16aa-4f38-9378-8847c0046d31
Journal backup:           inode blocks
Journal size:             128M
```


Booting from a LiveCD and running #fsck /dev/sda2 = returns clean. Please help if you can for I would really like to avoid re-installing the filesystem. I've searched the forums and goggled a bit but cant find a solution.


History:
I was moving some mp3 files from another disk to /dev/sda6 on /mnt/data and got an error "not enough disk space" ,strange I thought as I had some 50Gig free and was moving around 20Gig.........turns out it got sent to /dev/sda2 on / hence this error.

Additional:

```
[pete@desk ~]$ sudo fdisk -l
Password: 

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb95b67cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           4       32098+  83  Linux
/dev/sda2               5        1403    11237467+  83  Linux
/dev/sda3            3869        7771    31350847+  83  Linux
/dev/sda4            7772       19929    97659135    5  Extended
/dev/sda5            7772        7835      514048+  83  Linux
/dev/sda6            7836       14209    51199123+  83  Linux
/dev/sda7           14210       17379    25462993+  83  Linux
```

```
[root@desk /]# mount
/dev/sda2 on / type ext3 (rw)
none on /dev type ramfs (rw)
none on /proc type proc (rw)
none on /sys type sysfs (rw)
none on /proc/bus/usb type usbfs (rw)
none on /dev/pts type devpts (rw)
none on /dev/shm type tmpfs (rw)
/dev/sda1 on /boot type ext2 (rw)
/dev/sda3 on /home type ext3 (rw)
/dev/sda6 on /mnt/data type ext3 (rw)

```

---

### Post by bingoUV on 2008-05-11
1. Did you try after rebooting? When you booted into live CD, then came back to your installed OS, did you check this size reported by df again?

2. If outward appearances are fine, fsck does not bother to really check the filesystem. From your live CD, do this to make it check every byte of the partition : 
```

fsck.ext3 -f /dev/sda2 

```

3. Mount the partition (1st and second command below) when you are booted into live CD, and run df again (3rd command below)
```

mkdir /media/slash
mount /dev/sda2 /media/slash
df -h

```
Does it show around 10GB here too?

---

### Post by SnakeHips on 2008-05-11
> **bingoUV said:**
> 1. Did you try after rebooting? When you booted into live CD, then came back to your installed OS, did you check this size reported by df again?

2. If outward appearances are fine, fsck does not bother to really check the filesystem. From your live CD, do this to make it check every byte of the partition : 
```

fsck.ext3 -f /dev/sda2 

```

3. Mount the partition (1st and second command below) when you are booted into live CD, and run df again (3rd command below)
```

mkdir /media/slash
mount /dev/sda2 /media/slash
df -h

```
Does it show around 10GB here too?

Thanks for your speedy reply.

1. Sure ,yes i've tried a couple of times ,what is a real pain is i cant *see* what is taking up the space. 

2. ```

fsck.ext3 -f /dev/sda2 

``` reports: /dev/sda2: 118601/1400768 files (0.7% non-contiguos) 2531568/2809366 blocks.

3. Yes it shows around 10Gig here too :-(

          size  used   avail    

none      502M   0      502M    0%      /dev/shm
dev/sda2  11G   9.5G    647M    94%     /mnt/slash

....mind boggling ,is a re-install of the filesystem the *only* way out ?

---

### Post by bingoUV on 2008-05-11
Having to reinstall will be unfortunate. From gparted on a live CD, try shrinking the partition a little, and expanding it again. Hoping this would make the filesystem realize the folly of its ways.

---

### Post by SnakeHips on 2008-05-11
> **bingoUV said:**
> Having to reinstall will be unfortunate. From gparted on a live CD, try shrinking the partition a little, and expanding it again. Hoping this would make the filesystem realize the folly of its ways.

I shrunk the partition ,no change ,i'll have a go at expanding it next.

```
[root@desk pete]# cd /
[root@desk /]# df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             10776520   9950604    497468  96% /
none                    513480         0    513480   0% /dev/shm
/dev/sda1                31077      9036     20437  31% /boot
/dev/sda3             30857272   7733960  21869280  27% /home
/dev/sda6             50795348   5885408  42349984  13% /mnt/data
```

mutters to self........is their actually any data taking up the space? or are the blocks being "masked"/"locked" from being available due to a failed process?

---

### Post by bingoUV on 2008-05-11
A reboot fixes locked space by failed processes. If any process died leaving temporary files behind, that should show in du.

No idea what is wrong.

---

### Post by SnakeHips on 2008-05-11
> **bingoUV said:**
> A reboot fixes locked space by failed processes. If any process died leaving temporary files behind, that should show in du.

No idea what is wrong.

Guess I'm expecting to find some 8Gig .tmp file(s) which i can then deal with.......or something like the .chk files on FAT32 filesystem - at least it would be clear what needs to be cleaned! - right now I cant *see* what I'm up against.:confused:

---

### Post by SnakeHips on 2008-05-12
Ok ,so some further digging around and i ended up plugging the Disk back in that I originally transferred the data from.....and lo and behold I could see the data from this disk and managed to clean up /dev/sda2. The data was locked/hidden from me.

I've also found a link to a crash core (1Gig) that resides in /proc/Kcore so i'll take a look at that later...

---

### Post by chrisccoulson on 2008-05-12
> **SnakeHips said:**
> Ok ,so some further digging around and i ended up plugging the Disk back in that I originally transferred the data from.....and lo and behold I could see the data from this disk and managed to clean up /dev/sda2. The data was locked/hidden from me.

I've also found a link to a crash core (1Gig) that resides in /proc/Kcore so i'll take a look at that later...

/proc/kcore is your RAM. Don't try and delete it (I don't think you can anyway), it doesn't occupy any space on your disk

---

