---
title: "Teamviewer stopped working"
date: 2017-04-02
forum: General Help
---

### Post by Jason_Hunter on 2017-04-02
Just today my teamviewer stopped working and Im not able to start it, Ubuntu 16.10

I've even tried restarting the computer. 

I tried to strace it and it says something about inappropriate ioctl for device: 

```
("/home/b0ef/.local/share/teamviewer12/dosdevices/c:/windows/system32/wbem", {st_mode=S_IFDIR|0775, st_size=4096, ...}) = 0
stat64("/home/b0ef/.local/share/teamviewer12/dosdevices/c:/windows/system32/wbem/mscoree.dll", 0x33e2ac) = -1 ENOENT (No such file or directory)
open("/home/b0ef/.local/share/teamviewer12/dosdevices/c:/windows/system32/wbem", O_RDONLY|O_LARGEFILE|O_DIRECTORY) = 68
ioctl(68, VFAT_IOCTL_READDIR_BOTH, 0x222000) = -1 ENOTTY (Inappropriate ioctl for device)
close(68)                               = 0
open("/home/b0ef/.local/share/teamviewer12/dosdevices/c:/windows/system32/wbem", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 68
fstat64(68, {st_mode=S_IFDIR|0775, st_size=4096, ...}) = 0
getdents64(68, /* 6 entries */, 32768)  = 176
getdents64(68, /* 0 entries */, 32768)  = 0
close(68)                               = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [], 8) = 0
write(3, "\6\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\3\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\0\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [], 8) = 0
writev(3, [{"Z\0\0\0\204\0\0\0\0\0\0\0\30\0\0\0\0\0\0\2\0\0\0\0\0\0\0\0\204\0\0\0"..., 64}, {"S\0o\0f\0t\0w\0a\0r\0e\0\\\0M\0i\0c\0r\0o\0s\0o\0"..., 132}], 2) = 196
read(5, "\0\0\0\0\0\0\0\0(\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [], 8) = 0
writev(3, [{"_\0\0\0\32\0\0\0\0\0\0\0(\1\0\0\4\0\0\0\26\0\0\0\0\0\0\0\0\0\0\0"..., 64}, {"c\0F\0o\0r\0m\0a\0t\0T\0a\0g\0s\0", 22}, {"\1\0\0\0", 4}], 3) = 90
read(5, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
```

---

### Post by Jason_Hunter on 2017-04-02
I've also tried to remove and reinstall it, but it's still the same, really weird.

---

### Post by sp40140 on 2017-04-02
Search Var/logs. you might find something there. also whaich version of teamviewer are you using. what verion of ubuntu and which kernel?

---

