---
title: "permisions, NAs and /etc/fstab"
date: 2008-02-16
forum: General Help
---

### Post by glok_twen on 2008-02-16
ok hunted high and low and i'm stuck on getting the permissions right. i'm mounting a samba share housed on buffalo nas. i keep getting these permissions on all the directories, even down a level for the share level:

drwxr-xr-x 1 root root 0 2008-02-15 08:17 postgres

and here is the fstab line:

//hs-dhtgl9dc/share  /mnt/smb-mnt-01/   smbfs    defaults,rw,umask=0000 0 0

experimented with all sorts of options and still can't get to w's for the other 2 slots that are dashes above. and the result is that through pgadmin i can't create a new table space. i keep getting an error saying it can't set permissions on /mnt/smb-mnt-01/postgres.

can you help? should i being mounting nas in fstab? (yes i have ntfs-3g installed; and best i can tell the share is set up as read/write in the buffalo set up screens).

---

