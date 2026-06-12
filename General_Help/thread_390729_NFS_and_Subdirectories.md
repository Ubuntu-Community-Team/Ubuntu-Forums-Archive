---
title: "NFS and Subdirectories"
date: 2007-03-22
forum: General Help
---

### Post by skd5aner on 2007-03-22
Hi,

  I have 2 edgy servers.  I have one setup to export a directory structure via NFS and another to mount that directory structure.  I can mount everything just fine.  The directory structure has the same permissions, owner, and group all the way down.  However, when I try to go 2 levels down, it says the owner and group is root on the client but on the server it's correctly labeled with the correct owner and group.

Here's my /etc/export
/mythtv 192.168.1.201(rw,async)

Here's my /etc/fstab
192.168.1.200:/mythtv /mnt/mythtv nfs rsize=8192,wsize=8192,soft,actimeo=0 0 0

Here's the permissions on the server:
/mythtv/recordings# ls -la
total 36
drwxr-xr-x 4 mythtv mythtv  4096 2006-12-31 00:09 .
drwxr-xr-x 3 mythtv mythtv  4096 2006-12-31 00:09 ..
drwxr-xr-x 2 mythtv mythtv  8192 2007-03-22 10:02 area1
drwxr-xr-x 2 mythtv mythtv 12288 2007-03-22 10:36 area2

Here's what I see on the client with the mount:
/mnt/mythtv/recordings$ ls -la
total 16
drwxr-xr-x 4 mythtv mythtv 4096 2006-12-31 00:09 .
drwxr-xr-x 3 mythtv mythtv 4096 2006-12-31 00:09 ..
drwxr-xr-x 2 root   root   4096 2006-12-31 00:09 area1
drwxr-xr-x 2 root   root   4096 2006-12-31 00:09 area2

I'm totally confused... any help would be completely appreciated.

---

### Post by kidders on 2007-03-22
Hi there,

That certainly does seem odd! The apparent (client-side) "area1" & "area2" directory sizes (4096) are suspicious though... do you cross into another filesystem at that point?

Essentially, I'm wondering whether the server's /mythtv/recordings/ and /mythtv/recordings/area1/ are in the same filesystem.

---

### Post by skd5aner on 2007-03-22
> **kidders said:**
> Hi there,

That certainly does seem odd! The apparent (client-side) "area1" & "area2" directory sizes (4096) are suspicious though... do you cross into another filesystem at that point?

Essentially, I'm wondering whether the server's /mythtv/recordings/ and /mythtv/recordings/area1/ are in the same filesystem.

Wow... you hit the nail on the head.  I didn't even think about this (still a linux newb).  /mythtv/recordings/ is under "/" but /mythtv/recordings/areaX are each their own partition on their own hard disks.

To fix this, I exported both of the directories individually and it worked.  Thank you so much for taking the time to actually read and reply to my request for help!

---

### Post by kidders on 2007-03-22
Hey again,

> **skd5aner said:**
> To fix this, I exported both of the directories individually and it worked.Perfect. The reason for needing to do this is complicated, but suffice it to say that's the solution. What you were seeing client-side is what the server's /mythtv/recordings/ directory would look like if you'd forgotten to mount the various "area" filesystems.

> **skd5aner said:**
> Thank you so much for taking the time to actually read and reply to my request for help!Hehe no problem. :-)

---

