---
title: "ZFS Help!!!!!"
date: 2017-01-12
forum: General Help
---

### Post by serverman2020 on 2017-01-12
Hi Guys,

Ubuntu semi-newbie here.... running a Ubuntu 16.04 system and have recently followed this guide to set up a zfs share. 

[https://www.latentexistence.me.uk/zfs-and-ubuntu-home-server-howto/](https://www.latentexistence.me.uk/zfs-and-ubuntu-home-server-howto/)

It was fantastic for the last 6 months - no problems at all. Not sure what I did, but all of a sudden files started to go missing and although I could view some files, I could not write to the drive on the network. 

I think this may have happened after I ran apt-get update && upgrade... but from what I understood, ZFS is supposed to be now natively supported on Ubuntu 16.04???

The file structure is 

                         Data
                                 -> Music
                                 -> Movies
                                 -> Photos
                                 -> Misc (unlike the previous two, this folder among others was not made by terminal command 'zfs create' but with mkdir from terminal)

The folders that were created by mkdir have gone missing.

Running the command 'zfs mount -a' i get: "cannot mount, 'data' is not an empty directory". But when I run 'zfs list' I can see all the folders except mkdir folders.

Finally when running 'zfs mount -O data' everything is available, including the zfs directories and the directories made within 'data' with mkdir.

How has this happened?? I'm hoping it's simply just a mount issue... Would really appreciate any help with this - its driving me nuts!!

Thanks!

---

### Post by kpatz on 2017-01-12
When you used mkdir to create the misc directory, you probably didn't have data mounted at the time, so you created the directory under the mount point.  ZFS won't mount to a non-empty mountpoint directory.

Unmount all your ZFS mounts with 'zfs umount -a', then look in your data directory.  It should be empty.  If it's not, delete or move whatever's inside it so it is empty.  Then try 'zfs mount -a' again.

Once it's mounted, I'd use zfs create to create data/misc (it's not recommended to store files or directories inside the pool file system, just put other file systems there), then move whatever you had in the misc directory into there.

---

