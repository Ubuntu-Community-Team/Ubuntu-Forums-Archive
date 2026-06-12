---
title: "Mountning, dual boot"
date: 2013-02-23
forum: General Help
---

### Post by Grabbe on 2013-02-23
Hello ):P

I would like to have a dual boot-Linux and need help with my Ubuntu automatic mounting. I have important documents which I want to access and control from both OS. Last week I tried to edit fstab and so on... but errors while starting Ubuntu came up, like it couldn't mount my drive - but it was mounted when I logged in? Not properly though.

Here is what I want:

I want a partition (got a spare one with 100GB, not formatted right now though) which is automatically mounted when Ubuntu boots up. I want to own the drive/partition from Ubnutu (and the other OS later as well - don't need help with that though) so I can do whatever I want with it - and the mounted drive should be represented by a folder called myfiles in my Ubuntu-home-folder. Also I want to OWN this folder, because last time it was owned by root (though I fixed this with chroot, but then somehow the files started ending up on my Ubuntu-partition and not in the folder?!). Then I want my Downloads, Music, Videos-folders etc. to exist in the mounted partition. :)

I don't know if I explained it right, but I'm doing my best.

This is my fstab from last week. It didn't work properly. I also tried editing nouser/user and so one. 

/dev/sda8       /home/anonymous/myfiles  ext4    nouser,auto,uid=1000,gid=1000		0       0

---

### Post by ajgreeny on 2013-02-23
If you have the same username and GUID in both OSs you should be able to mount the partition with a fstab line in the format
```
UUID=e2554df2-7e16-4864-97c9-834d8bebecda /path/to/mount/folder ext4 defaults,relatime 0 2
```It is safer to use the UUID of the partition, not the /dev/sdx#, as the UUID will always remain the same until you re-format the partition.

If your username and GUID are the same in both OSs you can use chmod in one OS to change ownership and permissions as needed and it should also then be the same in the other OS.

PS: What is the "other" OS?

---

### Post by Grabbe on 2013-02-23
Arch Linux. But I just installed it. To sort of... try to learn when I've got time. But Ubuntu - I use all the time. :P Sort of.

Ok, so I should find out the UUID of the partition and mount it with the command you supplied? Will this make root or me owner? Shall I use chmod or chown?

Just saw thatI wrote chroot in my main post. But I meant to write chown.

---

### Post by schragge on 2013-02-23
To find out the UUID of the partition, run
```
blkid -ps UUID /dev/sda8
```

---

### Post by oldfred on 2013-02-23
What UID, GID is the standard in ARCH? Even if user name is the same if UID is not 1000 you will have issues.

       Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

### Post by Grabbe on 2013-02-26
Checking the UUID and using the posted fstab-line fixed everything for me, exactly the way I wanted it to be. Thanks!

Grabbe out.

---

