---
title: "creating directories on /dev/md0"
date: 2019-02-14
forum: General Help
---

### Post by fewjr on 2019-02-14
Hello,
     I am having a hard time understanding how to use a raid device for storage. The whole idea was to have a ssd boot drive and four, 2TB drives in a raid array for whatever I needed stored. So far I have been trying to use the server for Plex. Right now I have Ubuntu server installed on sda. What I am trying to figure out is how to make directory structure on /dev/md0, like /photos, /movies, /music, etc. Then I want to move the appropriate media files to the raided partition from my external drive. 

```
goblin@goblinservant:/$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda      8:0    0 111.8G  0 disk
&#9492;&#9472;sda1   8:1    0 111.8G  0 part  /
sdb      8:16   0   1.8T  0 disk
&#9492;&#9472;md0    9:0    0   1.8T  0 raid1 /mnt
sdc      8:32   0   1.8T  0 disk
&#9492;&#9472;md0    9:0    0   1.8T  0 raid1 /mnt
sdd      8:48   0   1.8T  0 disk
&#9492;&#9472;sdd1   8:49   0   1.8T  0 part
sde      8:64   0   1.8T  0 disk
&#9492;&#9472;sde1   8:65   0   1.8T  0 part
sdj      8:144  0 931.5G  0 disk
&#9492;&#9472;sdj1   8:145  0 931.5G  0 part  /home/goblin/secondary-hard-drive
sr0     11:0    1  1024M  0 rom
```
 
I only have two of the 2TB drives in the raid1 array right now, and it is mounted. sdj is the external drive. There is a folder on that drive called Music for example. How do I get the music folder onto md0?

Thank you
fewjr

---

### Post by CatKiller on 2019-02-14
You don't create anything in /dev. That's not a file or directory, that refers to the device itself.

You would mount the filesystem somewhere. Then you can access the files on that filesystem through its mount point.

---

### Post by #&amp;thj^% on 2019-02-14
> **CatKiller said:**
> You don't create anything in /dev. That's not a file or directory, that refers to the device itself.

You would mount the filesystem somewhere. Then you can access the files on that filesystem through its mount point.

+1 :)
> **fewjr said:**
>  What I am trying to figure out is how to make directory structure on /dev/md0, like /photos, /movies, /music, etc. 
Thank you
fewjr
And to add to it a little bit, This example:
```

mkdir -p /abcd/efgh/ijkl/mnop/qrst/uvwx/yz/
```
I think you know to change "/abcd/efgh/ijkl/mnop/qrst/uvwx/yz/" to the proper paths.
mkdir is "make directory"

The -p option creates the parent directories if they do not already exist.

If you want it to show you the directories it created while it is working then use verbose with it as shown below:
```
mkdir -pv /abcd/efgh/ijkl/mnop/qrst/uvwx/yz/ 
```  
If you find that you need to recover your "Music Folder" Foremost is a great option.
Found here: [https://help.ubuntu.com/community/DataRecovery#Foremost](https://help.ubuntu.com/community/DataRecovery#Foremost)

---

### Post by deadflowr on 2019-02-14
Work in /mnt since that's where the md0 raid1 partitions(?) are already mounted.

---

### Post by aromo2 on 2019-02-14
Have you formatted the partition?
```
mkfs.xfs /dev/md0
```

---

### Post by fewjr on 2019-02-14
Thank you for all the quick responses.
      I know that md0 isn't a file our directory. I was putting that post together right before I rushed off to work but I figured you'd get the idea what I was trying to figure out. 
     sdb & sdc are my raid devices and they are mounted at /mnt like @deadflowr said. They should already be formatted to ext4 but it doesn't show it there with lsblk. I'm still in the process of figuring out what I'm doing. As far as raid goes, I've been having a hard time understanding the steps involved after creating the raid array, to be able to use it just like any other drive. I will check the file system when I get home @aromo2.

fewjr

---

### Post by fewjr on 2019-02-14
so yes, it has a file system.

goblin@goblinservant:~$ sudo mkfs.ext4 /dev/md0
[sudo] password for goblin:
mke2fs 1.44.1 (24-Mar-2018)
/dev/md0 contains a ext4 file system
        last mounted on Thu Feb 14 12:12:48 2019

---

