---
title: "Mounting Permissions"
date: 2008-05-24
forum: General Help
---

### Post by ThomasWii on 2008-05-24
Hi, today i wanted to change my external hd from nfts to ext3, i backed up all the stuff from the nfts and reformatted it, then, using a shell script i made, i mounted them (this was in a root terminal) and went to put all the backed up stuff back on, but i got a permission error, so what i want to do is make it so when i mount it, it give full permission to every user, but what i don't want to do is to go playing around with the fstab.

Heres the shell script:```
#!/bin/bash

echo "This will mount the file's with propper loction"
umount -a
rmdir --ignore-fail-on-non-empty /media/disk
rmdir --ignore-fail-on-non-empty /media/disk-1
rmdir --ignore-fail-on-non-empty /media/sda1
echo "All have been unmounted"
mkdir /media/disk-1
echo "ExHard Drive File's Folder has been made"
mkdir /media/disk-2
echo "Debian Folder has been made"
mount /dev/sdb1 /media/disk-1
echo "ExHard Drive File's has been mounted"
mount /dev/sdb2 /media/disk-2
echo "Debian has been mounted"
mount-docs
```

Thanks in advance
Thomas.

---

### Post by geo909 on 2008-05-24
Sorry if I didn't understand very well, if my post doesn't answer your question just ignore it:

 When it comes to folders inside "/media", except from the permissions 
(chmod 700 etc) you sometimes have to change the owner/group too.
If the owner (and/or group, I'm not sure) is set to "root", I'm pretty sure you will only have read permissions, even if you "chmod 777" on that file.

Are the folders you are trying to mount your ext3 disk owned by you?

---

### Post by ThomasWii on 2008-05-24
Thanks for your reply, the owner is root, and in root a tried chmod 777 and chmod 555 and others and it did not work.

Thanks
Thomas

---

### Post by geo909 on 2008-05-24
> **ThomasWii said:**
> the owner is root, and in root a tried chmod 777 and chmod 555 and others and it did not work.


Can you try to change the actual user?
That is
```
sudo chown <yourusername> /media/yourfolder
```

---

