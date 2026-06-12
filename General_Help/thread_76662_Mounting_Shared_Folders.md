---
title: "Mounting Shared Folders"
date: 2005-10-15
forum: General Help
---

### Post by SpiKeRs on 2005-10-15
Hi i want to mount my windows shared folders from over my network when I run Ubuntu on my other machine. I can access the folder normally with nautilus like so: smb://compname/sharedfolder

However I am not sure how to mount it. I understand you have to put something into fstab file and have given it a go but it always says that the shared folder does not exist. This is what I have put in fstab:

//compname/sharedfolder   /media/sharedfolder   ntfs   nls=utf8,umask=0222   0          0

Any ideas?

---

### Post by Hikaru79 on 2005-10-15
You can't simply mount an SMB volume as 'ntfs'. Have a look at the package:
```
sudo apt-get install smbfs
``` then read up on that. Once you do that, it'll be very very simple to mount them :) Enjoy!

---

### Post by SpiKeRs on 2005-10-15
Thx for the pointer, have it  working now

---

### Post by zekolas on 2005-10-15
The command I use is 
smbmount //computername/sharefolder /mnt/shared

---

