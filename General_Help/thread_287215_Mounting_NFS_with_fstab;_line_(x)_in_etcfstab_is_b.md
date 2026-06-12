---
title: "Mounting NFS with fstab; line (x) in /etc/fstab is bad?"
date: 2006-10-28
forum: General Help
---

### Post by darthtard on 2006-10-28
I'm trying to get an NFS share to mount through fstab.  When I attempt this i get this error:

[mntent]: line 10 in /etc/fstab is bad
[mntent]: line 11 in /etc/fstab is bad

My fstab files looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb4       /home           ext3    defaults        0       2
/dev/sdb3       /var            ext3    defaults        0       2
/dev/sdb1       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
192.168.2.105:/Volumes/El\ Gordo/Share                          /mnt/share      nfs     rw,rsize=32768,wsize=32768,hard,intr    0       0
192.168.2.105:/Volumes/Gordito/BKUP/New\ Folder/My\ Pictures    /mnt/pix        nfs     rw,rsize=32768,wsize=32768,hard,intr    0       0

I can mount the directories manually using mount.  Perhaps there's an error in my fstab syntax I am not noticing?  If anyone can give me insight as to what the problem is here I'd much appreciate it.

Thanks in advance.

---

### Post by DaveBorealis on 2006-10-28
> **darthtard said:**
> 
192.168.2.105:/Volumes/El\ Gordo/Share                          /mnt/share      nfs     rw,rsize=32768,wsize=32768,hard,intr    0       0
192.168.2.105:/Volumes/Gordito/BKUP/New\ Folder/My\ Pictures    /mnt/pix        nfs     rw,rsize=32768,wsize=32768,hard,intr    0       0

Those spaces in the paths are probably the problem.  (Using networking commands on paths with spaces has never been much fun for me.)  What kind of OS is the NFS server?

Best regards,
Dave

---

### Post by taurus on 2006-10-28
Maybe you want to use the " " instead of \, i.e., "/Volumes/Gordito/BKUP/New Folder/My Pictures"!

---

### Post by darthtard on 2006-10-30
Thanks for the tips guys.  I tried tauris' suggestion and quoted my pathname; I didn't get an error with this configuration however the path still did not mount.  After deleting the pathname spaces and reconfiguring nfs both mounts loaded fine.  

To answer your question, Mr. Borealis, the NFS server is OSX Server 10.4.8.

Thanks again!

---

