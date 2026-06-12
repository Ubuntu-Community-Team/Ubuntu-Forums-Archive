---
title: "Switching modes in a dual mode usb device cdu680"
date: 2008-01-08
forum: General Help
---

### Post by yellowbread on 2008-01-08
I have a Franklin cdu680 usb modem which operates in two modes, a data mode and a modem mode.
It came with a program --itfchg, that switches the device from data to modem mode. From running strace on itfchg, I think that itfchg loads some stuff from a couple libraries, opens the device, then uses iotcl to change its mode. here's the exact output:

```
root@filbert-desktop:/home/filbert/Linux_Ubuntu# strace ./itfchg /dev/sdh
execve("./itfchg", ["./itfchg", "/dev/sdh"], [/* 39 vars */]) = 0
[ Process PID=6739 runs in 32 bit mode. ]
brk(0)                                  = 0x804a000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff7fa3000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(0x3, 0xffc26180)                = 0
mmap2(NULL, 80151, PROT_READ, MAP_PRIVATE, 3, 0) = 0xfffffffff7f8f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib32/libc.so.6", O_RDONLY)      = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260a\1"..., 512) = 512
fstat64(0x3, 0xffc26210)                = 0
mmap2(NULL, 1349136, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff7e45000
mmap2(0xf7f89000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x143) = 0xfffffffff7f89000
mmap2(0xf7f8c000, 9744, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xfffffffff7f8c000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff7e44000
set_thread_area(0xffc26700)             = 0
mprotect(0xf7f89000, 4096, PROT_READ)   = 0
munmap(0xf7f8f000, 80151)               = 0
open("/dev/sdh", O_RDWR)                = 3
nanosleep({0, 800000}, NULL)            = 0
ioctl(3, FIBMAP, 0xffc26afc)            = 0
exit_group(0)                           = ?
Process 6739 detached

```

I would like to be able to figure out how to do on my own what the itfchg program does, because although the program runs fine in Gutsy, it won't run in Hardy alpha. If I'm in Hardy and for some reason the device gets switched to data mode, I have to reboot to Gutsy to reset it.

I've asked the people at Franklin about this with the reply "I apologize but we do not have access to this at this time.  Therefore, cannot go about changing the mode." I'm not quite sure exactly what that means, except that I will not be getting any help from them soon.

So, if anyone out there can help me figure this out, I would be very grateful.

---

