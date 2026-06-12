---
title: "Gutsy: mount options logic"
date: 2007-10-28
forum: General Help
---

### Post by mibadt on 2007-10-28
Hi,
I'm on a dual boot system.
Looking at my fstab, I've noticed everybody is granted FULL rights to my win partition which seems dangerous. What's the logic behind this? Why not limit this to myself only?

The appropriate fstab entry looks like:
UUID=CA7CADEF7CADD70B /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3


Am I correct assuming that if I'd like to change it to ead only for myself only, I should change the umask from 007 to 400?

Thanks

Michael Badt

---

### Post by jackocleebrown on 2007-10-28
Hi,

The umask sets permissions but if you want to be the only one to read/write you'll need to change the owner too.
Default is root owner, root group.
umask=007 lets root and everyone in the group 46 (gid=46) read/write/execute, others have no access.

To only allow you to read/write/execute change umask to 077 and add an option "uid=##" where ## is your user ID.

To allow others to read but not write and full access for your user, change umask to 027 and add an option "uid=##" where ## is your user ID.

[This]("http://gentoo-wiki.com/HOWTO_Mount_MS_Windows_partitions_(FAT,NTFS)#Mount_Options") might help 


give it a go, let me know if it works.

Jack.

---

### Post by mibadt on 2007-10-28
Thanks!
I'll try

Michael Badt

---

