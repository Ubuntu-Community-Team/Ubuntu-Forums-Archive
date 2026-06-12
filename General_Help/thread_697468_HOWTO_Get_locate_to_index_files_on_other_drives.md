---
title: "HOWTO: Get locate to index files on other drives"
date: 2008-02-15
forum: General Help
---

### Post by MegaJim on 2008-02-15
If like me and many other users you've moved to linux from another OS you're likely to have some other partitions/drives that are full of data you still need access to but for whatever reason you haven't created specific mount points for, you may not be aware that by default the /media path is excluded from the slocate indexer updatedb.

This prevents the user from being able to locate files on these drives using the locate command in a terminal

There are several ways of getting around this, each of which i'll briefly discuss with examples

Firstly you can change the /etc/updatedb.conf file to remove /media from the excluded list

```
sudo nano /etc/updatedb.conf
```

Find the line starting with PRUNEPATHS, mine on a default installation is

```
PRUNEPATHS="/tmp /usr/tmp /var/tmp /afs /amd /alex /var/spool /sfs /media"
```

This is fine because we don't want to index things like temporary files and dvds/cds that will provide invalid locate entries later on, however it does also exclude drives that are automatically mounted by ntfs-config and automount as these are also placed in /media

So removing /media from the prune path will work, but it will also result in truly external media being indexed as well which is bad.

The second method is to create symbolic links to your more permanent mounts in /mnt so as to allow updatedb to reach them here.

```
user@host:~$ cd /media
user@host:/media$ ln -s MountToBeIndexed/ /mnt/

Thirdly you could create static mount points for your drives in /mnt, but this requires reconfiguration if things change and is only for the truly anal among us (actually its what I do hehe).

Now all that is left to do is update the database and enjoy your new searching power!

[code]sudo updatedb
```

I hope somebody finds this useful!

---

### Post by K.Mandla on 2008-02-19
Moved to General Help.

---

### Post by sipickles on 2008-05-15
Thanks, works great..

... now if only the Tracker search tool could be so intelligent?

---

### Post by calin_014 on 2008-07-22
Second method does not work for me...it just bypasses the symbolic links in /mnt. Any ideeas?

---

