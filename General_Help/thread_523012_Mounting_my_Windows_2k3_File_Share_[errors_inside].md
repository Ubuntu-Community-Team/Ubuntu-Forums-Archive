---
title: "Mounting my Windows 2k3 File Share [errors inside]"
date: 2007-08-11
forum: General Help
---

### Post by COKE CAN on 2007-08-11
```
thegoodpirate@laptop:~$ sudo mkdir -p /mnt/ntserver
Password:
thegoodpirate@laptop:~$ sudo mount -t cifs //192.168.1.2/Music -o username=my.name,password=Password1 /mnt/ntserver
mount: block device //192.168.1.2/Music is write-protected, mounting read-only
mount: cannot mount block device //192.168.1.2/Music read-only
thegoodpirate@laptop:~$ 
```

Please help me understand what is going on.

---

### Post by TheExplorer on 2007-08-12
If you would like to mount your Windows partitions automatically everytime you boot into  Ubuntu then install the following packages with Synaptic:

> libfuse2
fuse-utils
libntfs-3g
ntfs-3g
ntfs-config

Then go to **Applications -> System Tools -> NTFS Configuration**

If you can't create Windows partition then there is a little trick:

Put a tick next to the desired partition, input 'Windows' or any other name and then click anywhere inside the list of available partitions.

Restart.

---

