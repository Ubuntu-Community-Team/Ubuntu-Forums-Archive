---
title: "after Dapper Update NFS/SMB don't work"
date: 2007-02-15
forum: General Help
---

### Post by Chachee on 2007-02-15
Hello all,
  I finally did the update to Dapper that's been there for a week.  Now I can't see my FreeNAS Server with SMB/NFS.  I can still reach it on my windows boxes with SMB.  My fstab file, which didn't change is -

 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

#NFS Share Mounts
server:/mnt/Music /media/music   nfs     rsize=8192,wsize=8192,timeo=14,intr
server:/mnt/Backup /media/backup   nfs     rsize=8192,wsize=8192,timeo=14,intr
server:/mnt/Videos /media/videos   nfs     rsize=8192,wsize=8192,timeo=14,intr


I issues the 'sudo mount -a' command and I get

mount to NFS server 'server' failed: server is down

The server isn't down.  None of the folder will come up in network browser either.

Need some help, everything worked fine before I updated 20 minutes ago.

Thank you.

JT

---

### Post by Chachee on 2007-02-16
So,
  As an update I went and checked out:

[http://www.linux.org/docs/ldp/howto/NFS-HOWTO/](http://www.linux.org/docs/ldp/howto/NFS-HOWTO/)

  But it really didn't give me any information.  The worst part is I can't even get on the samba shares the rest of my windows computers could see and I could do that before I even set up NFS.

Stupid update.

JT

---

