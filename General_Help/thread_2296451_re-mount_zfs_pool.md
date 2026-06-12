---
title: "re-mount zfs pool"
date: 2015-09-25
forum: General Help
---

### Post by masonje2 on 2015-09-25
I just upgraded from 14.04 to 14.10 to 15.04 and through that, I lost my zfs pool mounts.  I still see the disk members there:

NAME                  FSTYPE        SIZE MOUNTPOINT    LABEL
sda                                 1.8T               
&#9500;&#9472;sda1                zfs_member    1.8T               datastore
&#9492;&#9472;sda9                                8M               
sdb                               931.5G               
&#9500;&#9472;sdb1                zfs_member  931.5G               datastore
&#9492;&#9472;sdb9                                8M               
sdc                                 1.4T               
&#9500;&#9472;sdc1                zfs_member    1.4T               datastore
&#9492;&#9472;sdc9                                8M               

I followed this article to set it up
[http://www.jamescoyle.net/how-to/478-create-a-zfs-volume-on-ubuntu](http://www.jamescoyle.net/how-to/478-create-a-zfs-volume-on-ubuntu)

My question is, how do I re-mount the devices without trashing things?  I just wasn't sure if I re-ran the command:  zpool create -f datastore raidz /dev/vda /dev/vdb /dev/vdc .... what would happen. 

Thanks!

---

### Post by lukeiamyourfather on 2015-09-28
Don't create the pool again if you want to keep data already on the pool. Creating a new pool will wipe the drives. See my post in another thread for example commands for importing a pool with existing data.

[http://ubuntuforums.org/showthread.php?t=2292524&p=13353085#post13353085](http://ubuntuforums.org/showthread.php?t=2292524&p=13353085#post13353085)

---

