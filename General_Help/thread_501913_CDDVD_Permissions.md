---
title: "CD/DVD Permissions"
date: 2007-07-15
forum: General Help
---

### Post by complexgeek on 2007-07-15
Hi.
I'm having a strange problem with mounting some DVD+R discs in Kubuntu 7.04.

Some discs work fine, having read & execute permissions for all users.
```

-r-xr-xr-x 1 root root 365404160 2005-09-29 20:13 File A.avi
-r-xr-xr-x 1 root root 368132096 2005-09-30 13:20 File B.avi
-r-xr-xr-x 1 root root 365793280 2005-10-16 01:35 File C.avi

```

But some produce a listing like:
```

-rwx------ 1        502        502 366587904 2006-01-26 08:22 File 1.avi
-rwx------ 1        502        502 366880768 2006-02-01 19:24 File 2.avi
-rwx------ 1        502        502 366807040 2006-03-21 13:11 File 3.avi

```
They don't seem to have an owner or group, and the files can only be accessed via root.

Is there a way I can force the mode to 555, like I can do for a SMB share with the file_mode option?

Thanks.

---

### Post by kuja on 2007-07-16
I've run into this problem with a select few disks also (IIRC, my Quake4 disks are like that), unfortunately I never found a solution :(

---

