---
title: "Mounting an encrypted volume in Gutsy with True Crypt"
date: 2007-11-03
forum: General Help
---

### Post by klineroger4 on 2007-11-03
Hi everyone...
I have downloaded and installed True Crypt on my machine (Dell 1501, AMD 64, Gutsy). The install went fine. I then used the wizzard to create my encrypted volume (5mb). Then I created a directory to mount it in, Here is my issue:

~$ truecrypt -u XXXXXX.tc  YYYYYY (where X is the name of the volume and Y is the name of the directory)
Enter users or root's system password: 
Cannot open volume: No such file or directory

The directory and the volume exist, as I can see them in my home folder. I have used and looked at guides from multiple sites and followed all the directions. But I keep ending up at this error. Can anyone provide any assistance? Thanks!

---

### Post by Trevster on 2007-11-04
Hi, not sure if this will help you but I will post the commands I use to mount my volumes.

For a truecrypt partition at sda6 to be mounted at /mnt/tc/:

```
truecrypt  -u /dev/sda6  /mnt/tc/
```

For a usb drive with a ntfs  truecrypt volume called my stuff to be mounted at /mnt/tc2/:

```
truecrypt -u --filesystem ntfs-3g  /media/disk/truecrypt/my\ stuff /mnt/tc2/
```

Good luck.

---

