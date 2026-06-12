---
title: "Unable to change ownership of directory."
date: 2006-12-06
forum: General Help
---

### Post by ronniez on 2006-12-06
Hi I'm trying to ownership for a particular folder, but I always get the following error:
root@compie:/media/sdb1# chown user_me:users smb_share
chown: changing ownership of `smb_share': Operation not permitted

However I'm logged in as root.

I would like to share that folder between Linux and windows box. It is a FAT32 partion, sharing of a folder underneath the users home folder does work.

the specific folders at the mount point:
drwxrwxrwx 5 root root 8192 1970-01-01 01:00 .
drwxr-xr-x 7 root root 4096 2006-10-25 15:26 ..
drwxrwxrwx 4 root root 8192 2006-12-03 13:13 smb_share

It is mounted the following way (fstab):
UUID=C067-63E6  /media/sdb1 vfat umask=000,codepage=850,iocharset=iso8859-15 0 0

Which then shows up like this:
/dev/sdb1 on /media/sdb1 type vfat (rw,umask=000,codepage=850,iocharset=iso8859-15)

The default mount command hat the same issue.
UUID=C067-63E6  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1

Running ubuntu 6.10 (edgy) 64 on core2 duo.

Thanks in advance.

---

### Post by steve.horsley on 2006-12-06
You can't change ownership on FAT partitions because the FAT filesystem doesn't store file owner and group information. I think this is where gid= comes in, and there is another option to mount that sets the owner for every file on the partition. 

Since you have set umask=000, every Ubuntu user should have access. Why the need to change owner?

---

### Post by ronniez on 2006-12-07
Hmm, don't know what acually happend, but now I'm able to access the shared directory from the windows box right now. So for now issue solved however I do not know the reason :neutral: , maybe because of the reboot or sharing a different directory did set some things which went wrong once before.

---

