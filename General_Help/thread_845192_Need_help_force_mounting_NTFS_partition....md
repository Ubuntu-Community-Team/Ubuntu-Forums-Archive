---
title: "Need help force mounting NTFS partition..."
date: 2008-06-30
forum: General Help
---

### Post by spotdog14 on 2008-06-30
Hello, I am running a live cd of Ubuntu 7.10. I am attempting to repair a coworkers HP laptop that gets a BSOD, I have found the fix for windows, i simply need to replace a .dll file. But since the computer keeps BSODing i cannot get windows to "safely shutdown" so when ever i try to open the NTFS partition under Ubuntu it says that I cannot. 

So mount box after the error tells me to do this, and this is the result:

```

spotdog14@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda1 /media/disk -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/disk: No such file or directory
spotdog14@ubuntu:~$ 

```

What do I do?

---

### Post by drs305 on 2008-06-30
If there is no /media/disk mountpoint, make one with the following command:
```

sudo mkdir /media/disk
```

---

### Post by spotdog14 on 2008-06-30
> **drs305 said:**
> If there is no /media/disk mountpoint, make one with the following command:
```

sudo mkdir /media/disk
```

Great, thank you very much. That seems to have done the trick. Now I guess that was the easy part. I am getting error after error on the Win install. I keep getting Stop: 0x0000221 errors. I think I am going to tell him to get my an external HDD and copy over all his files then do a reformat, and since I do not think that he has his windows cd's its Ubuntu all the way!

---

