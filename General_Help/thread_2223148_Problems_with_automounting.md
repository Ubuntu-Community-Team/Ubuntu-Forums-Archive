---
title: "Problems with automounting"
date: 2014-05-09
forum: General Help
---

### Post by steven-aj-oxley on 2014-05-09
I have been having problems with auto-mounting. There is a superuser question for it already here: [http://superuser.com/questions/751708/unrecognized-mount-option-fmask-0111-or-missing-value](http://superuser.com/questions/751708/unrecognized-mount-option-fmask-0111-or-missing-value). You can view the details there. The gist is that it's saying that an 'fmask' value is invalid or something, but I'm pretty sure it's valid from looking at the mount documentation. And I only started seeing issues after restarting the computer (again, see details in the superuser question). Does anyone have any ideas?

---

### Post by deadflowr on 2014-05-09
I think it's self-explanatory.
```
mount:** wrong fs type, bad option**, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail or so

```

Try changing it to simply "defaults"
From
```
UUID=45099f0b-8d10-4fd7-8214-b0a070dc0be7  /mnt/share  ext4 ** errors=remount-ro,fmask=0111,dmask=0000**  0  2
```
To
```
UUID=45099f0b-8d10-4fd7-8214-b0a070dc0be7  /mnt/share  ext4  **defaults**  0  2
```

Edit: More options here
[https://help.ubuntu.com/community/Fstab#Options](https://help.ubuntu.com/community/Fstab#Options)

---

