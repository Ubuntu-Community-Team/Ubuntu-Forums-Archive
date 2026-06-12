---
title: "How to deny access rights to NTFS partitions (Ubuntu 8.04)"
date: 2008-05-03
forum: General Help
---

### Post by Matiee on 2008-05-03
I just upgraded to Hardy and want to set up a multiuser environment.
I have some NTFS partitions to which I want esclusive access for the only users that belong to **ntfs-users** (group created by me, gid=2000)

As I did in Gutsy, I opened up */etc/fstab* and corrected the option **gid=46** to **gid=2000**

Here is an extract from fstab from Gutsy:
> # /dev/sda1
/dev/sda1     /mnt/.windows_1       ntfs-3g     defaults,umask=007,gid=2000     0 0
# /dev/sda5
/dev/sda5     /mnt/.windows_2       ntfs-3g     defaults,umask=007,gid=2000     0 0

# /dev/sda6
/dev/sda6     /mnt/.windows_junk   ntfs-3g    defaults,umask=007,gid=2000      0 0

# /dev/hdb1
/dev/hdb1     /mnt/.backup            ntfs-3g     defaults,umask=007,gid=2000      0 0

And here is an extract from fstab from hardy:
> # /dev/sdc1
/dev/sdc1     /mnt/.windows_1       ntfs     defaults,umask=007,gid=2000     0 1
# /dev/sdc5
/dev/sdc5     /mnt/.windows_2       ntfs     defaults,umask=007,gid=2000     0 1

# /dev/sdc6
/dev/sdc6     /mnt/.windows_junk   ntfs    defaults,umask=007,gid=2000      0 1

# /dev/sdb1
/dev/sdb1     /mnt/.backup            ntfs     defaults,umask=007,gid=2000      0 1



Now, the problem is: this worked very well with Gutsy but **no longer** works with Hardy.

In Hardy, I can remove the gid of the mount point from every group,
I can even use the option **umask=777** to deny every kind of right to every user in the system (even to root), 
but in that case too, every normal unprivileged user will have read/write access to every NTFS partition.

I hope this was clear, sorry for my so-so english...:oops:

How can I solve this? is this a bug?

---

### Post by Matiee on 2008-05-04
Still nothing? :(

---

### Post by Matiee on 2008-05-05
So really, doesn't anybody know anything about this thing? :-|

Can at least someone tell how to set up ntfs-3g so that normal users couldn't use it?

In have to be possible: in Gutsy this worked.

---

### Post by debone on 2008-05-16
Hi,
you could download PySDM, a graphical user interface which will edit the fstab file.
Haven't used it myself yet, but it seems to have all the options you need.
Succes

---

