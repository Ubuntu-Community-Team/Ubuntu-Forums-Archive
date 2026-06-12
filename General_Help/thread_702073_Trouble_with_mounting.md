---
title: "Trouble with mounting"
date: 2008-02-19
forum: General Help
---

### Post by nigel_salvador on 2008-02-19
I am unable to boot from my Linux partition

Instead of trying to fix the problem, which I have tried to do for the past week, I just want to  be able to mount the partition and retrieve my data since I've decided to install a new hard drive and install the latest version of Ubuntu.

Every time I try and mount the Linux partition using the mount command I get the following error, which prevents me from proceeding forward:

mount: wrong fs type, bad option, bad superblock on /dev/hdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

If there is anyone who has come across this problem and can help me out it would be greatly appreciated. Thank you in advance.

---

### Post by dcstar on 2008-02-19
> **nigel_salvador said:**
> I am unable to boot from my Linux partition

Instead of trying to fix the problem, which I have tried to do for the past week, I just want to  be able to mount the partition and retrieve my data since I've decided to install a new hard drive and install the latest version of Ubuntu.

Every time I try and mount the Linux partition using the mount command I get the following error, which prevents me from proceeding forward:

mount: wrong fs type, bad option, bad superblock on /dev/hdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

If there is anyone who has come across this problem and can help me out it would be greatly appreciated. Thank you in advance.

Post the following:
```
cat /etc/fstab
fdisk -l
```

---

