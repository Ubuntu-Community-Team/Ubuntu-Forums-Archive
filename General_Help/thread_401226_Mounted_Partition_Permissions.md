---
title: "Mounted Partition Permissions"
date: 2007-04-04
forum: General Help
---

### Post by sixfoottallrabbit on 2007-04-04
Hey,

I have the following line in my fstab file to mount one of my partitions, and I would like to have full access to it:

/dev/hda5 /mnt/files vfat rw,umask=0000,uid=1000,gid=sixfoottallrabbit 0 0

When I check the permissions in Nautilus it says:
"Create and Delete Files"
for all users.

"ls -l" on the mounted folder returns:
drwxrwxrwx 10 sixfoottallrabbit sixfoottallrabbit 32768 1970-01-01 01:00 files

However, most programs can not write to it.

**Will Work**
Nautilus works fine. I can add new files, delete files, edit files, etc.
wget will download files to it, fine.

**Won't Work**
Firefox WILL NOT download files to it.
I cannot compile many programs' source code because they need to be able to write to the partition, this does not work.
I cannot recieve files from aMSN to the partition.

How can I fix this? Is there something up with the permissions?

Thanks a lot

-sixfoottallrabbit

---

