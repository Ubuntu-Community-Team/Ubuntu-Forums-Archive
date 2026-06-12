---
title: "Mount ext4 formatted Raid1 Disk Array and file permissions questions"
date: 2019-10-02
forum: General Help
---

### Post by ozkan on 2019-10-02
Hi,

In /etc/fstab I have one line which is mounting an ext4 formatted Raid1Array in boot time:

/dev/md35 /depo35 ext4 defaults,nofail,discard,grpid

it mounts successfully no problem.

what I want to achieve is that: every newly created new file shall have myname : plugdev with file permissions wrxwrx.r.

in fstab grpid option is allowing me to give myname : plugdev ownership of every new file created because the parent folder is always myname : plugdev
but somehow ... system does not give proper permissions for newly created files, they are always rwxr..r.. although parent folder permission is wrxwrx.r.

what is the proper option to achieve it in fstab ? (I am looking for an option like umask as I do for ntfs partitions)

ps:myname is also belonging to plugdev

thanks

---

### Post by QIII on 2019-10-02
Duplicate of [https://ubuntuforums.org/showthread.php?t=2428303](https://ubuntuforums.org/showthread.php?t=2428303)

Closed.

---

