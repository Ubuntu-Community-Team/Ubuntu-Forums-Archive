---
title: "Cant accsess my new HDD"
date: 2017-06-20
forum: General Help
---

### Post by mac187 on 2017-06-20
Hi, i just installed new HDD to my laptop, now i have 2 HDD

First HDD -> 2 partition with Ubuntu alongside Windows

Second HDD -> Ment to be used for storage for everything, then i mean i want to read, write, delete, save FULL acsess to this hdd from Ubuntu

When i try to get acsess in the second HDD from ubuntu, i got this message:

Error mounting system-managed device /dev/sda3: Command-line `mount "/mnt/CE285B83285B6A0B"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda3': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.


How to solve this out? I'v been trying to google it but dident unserstand  :/ Anyone can help me out? THANX !

---

### Post by leunam12 on 2017-06-20
It seems that the hard drive has Windows installed and it is hibernated. Go to the terminal and, assuming that the partition that does not mount is /dev/sda3 as in your post above, type ```
sudo ntfsfix /dev/sda3
```then press enter. however, I find strange that your second drive is /dev/sda instead of /dev/sdb, are you sure you are trying to mount the secondary drive? It seems to me that you are trying to access your Windows partition on the primary drive; maybe?

---

