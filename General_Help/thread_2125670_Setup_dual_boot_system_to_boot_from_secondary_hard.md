---
title: "Setup dual boot system to boot from secondary harddrive"
date: 2013-03-14
forum: General Help
---

### Post by bg4m3r on 2013-03-14
I've recently done some major upgrades to my system and am trying to improve my disaster recovery options. Here is my current drive/OS configuration:

```

DriveA\
       -RAID 0+2 via MB controller (ASUS); Win7x64 installed (640GB) (Ubuntu 12.10 x86 installed as a VM in Windows)
DriveB/

DriveC -3 partitions, NTFS (768GB), ext4 (244GB), swap (12GB); Ubuntu 12.04 x64 installed + NTFS storage/backup
```

Currently using GRUB2 as bootloader.

Currently, the system boots from the RAID configuration. What I want is the option to boot from the secondary drive in the event the RAID or the drives within it fail and still be able to get into Ubuntu. How can I have GRUB2 installed (and maintained) on both drives?

---

### Post by dabl on 2013-03-14
I would like to see the output of this command (so I can understand your setup):

```
sudo blkid -c /dev/null -o list
```

---

