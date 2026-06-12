---
title: "Must be an easy task for you guys"
date: 2007-11-28
forum: General Help
---

### Post by elgaza on 2007-11-28
Hi

I am new to the Linux world I am an administrator for windows machine
and decided to dip into the Linux world and I love it.

but I just started and I have this little problem I have created a folder as root
and I would like to give a specific group read and write permission to this folder
I have tried to do as root chmod g+rwxs /media/sda5/Downloads but I still cant write as
a different user

please help.

thank you.

---

### Post by bettlebrox on 2007-11-29
Looking at the path I'd guess your accessing a removable drive?

If you are is is running a FAT (windows) filesystem? If yes, then FAT doesn't support Linux/UNIX permissions, and the only way you can modify the group permissions (of the whole FAT drive or partition) is at mount time.

Otherwise, what does "mount |grep /media/sda5/" show?

---

### Post by elgaza on 2007-11-29
Hi

this is what I get 

/dev/sda5 on /media/sda5 type vfat (rw,fmask=0133,dmask=0022,uid=0,gid=0)

---

