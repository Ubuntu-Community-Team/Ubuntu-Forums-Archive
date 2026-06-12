---
title: "Problem with Samba mounts"
date: 2005-05-29
forum: General Help
---

### Post by frj on 2005-05-29
Hi, 
Iam running samba in my homenetwork. From my slack10.1 computer there is no problem to mount the windows shares. 
But i cannot mount the windows shares from my ubuntu laptop.
The error msg is the same for all shares.
```
# mount -t smbfs -o username=gustav //gutsav/naruto ./Mounts/Gustav/Naruto/
[I]mount: wrong fs type, bad option, bad superblock on //gutsav/naruto,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/I] 
```I have checked that the samba package is installed, so there should not be any fs problem. 

*Ya see me and the lord have an understanding.*

---

