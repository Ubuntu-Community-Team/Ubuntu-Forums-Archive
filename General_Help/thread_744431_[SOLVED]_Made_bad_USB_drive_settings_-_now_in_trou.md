---
title: "[SOLVED] Made bad USB drive settings - now in trouble."
date: 2008-04-03
forum: General Help
---

### Post by dryder on 2008-04-03
Hi,
*MODERATORS et al: this post derives from a thread in HARDY forum but this problem evolved from another and does not belong in that forum/thread. *

I'm in desperate need of help please - I did something stupid to my usb drive I was having problems with. Thought I had the solution and clicked the drive icon, Properties>Volume and changed Settings> Mount Point, File System and Mount Options. OK - *now* I know I shouldn't have.

Now I can't access the drive - nor can gparted.
Although that is not quite true - if I:
> sudo mkdir /media/sdj1
sudo mkdir /media/"FreeAgent Drive"
sudo mount -t ntfs /dev/sdj1 /media/"FreeAgent Drive" -o rw,noexec,nosuid,nodev,sync,umask=222
the partition mounts and I can see the contents - so can gparted. 

fdisk -l gives:
> Disk /dev/sdj: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               1       60801   488384001    7  HPFS/NTFS
david@ubuntu-server:~$  and mtab shows > /dev/sdj1 /media/FreeAgent\040Drive ntfs rw,noexec,nosuid,nodev,sync,umask=222 0 0 when it is mounted using the method above. Nothing in fstab.

how can I undo the Settings Mount Point, File System and Mount Options which I shouldn't have made and restore it to normal?

David

---

### Post by dryder on 2008-04-03
RESOLVED - FAULTY DRIVE

My apologies everybody - what I thought was me turned out to be a faulty drive now being replaced.

David

---

