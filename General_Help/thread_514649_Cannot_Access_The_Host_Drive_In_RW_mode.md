---
title: "Cannot Access The Host Drive In R/W mode"
date: 2007-08-01
forum: General Help
---

### Post by Antman on 2007-08-01
Ok, after trying to search on the forum for someone else with this error, I figured I'd ask for assistance.

I normally run Ubuntu as a full install, but figured I'd try Wubi on my new laptop without doing the normal partitioning and stuff. :-\"

After I installed Wubi and rebooted, I received this nice error upon selecting the Ubuntu boot option:

```

e1000_Probe EEPROM Not Valid
Checksum is not Valid.
No Raid Disks


ERROR:


Cannot Access The Host Drive In R/W mode.
```

Has anyone seen this error before?

Hardware:
IBM T60 with SATA 40gig drive
ATI x1300
1gig Ram
Intel Wireless 3945abg

Thanks

---

### Post by ago on 2007-08-01
It generally means that ntfs is not clean. You probably need to run chkfs from windows

---

### Post by Antman on 2007-08-01
> **ago said:**
> It generally means that ntfs is not clean. You probably need to run chkfs from windows

Hmmm... so far I tried ```
chkdsk c: /r 
```to look for issues on the drive but that didn't work. I'll try some more fixes for the NTFS system and post my results.

Thanks

---

### Post by tuxcantfly on 2007-08-02
Does doing this work or give any more detailed output?:

```
sudo mkdir /media/ntfs
sudo ntfs-3g /dev/sda1 /media/ntfs
```

(I'm assuming /dev/sda1 is your ntfs partition, adjust the command accordingly)

---

