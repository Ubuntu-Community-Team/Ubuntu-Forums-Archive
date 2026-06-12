---
title: "QEMU Error"
date: 2006-12-18
forum: General Help
---

### Post by jrobinson5 on 2006-12-18
```
jrobinson@laptop:~/qemu/winxp$ qemu -boot c -hda winxp.img -m 256 -snapshot
You do not have enough space in '/dev/shm' for the 256 MB of QEMU virtual RAM.
To have more space available provided you have enough RAM and swap, do as root:
umount /dev/shm
mount -t tmpfs -o size=272m none /dev/shm
Or disable the accelerator module with -no-kqemu
jrobinson@laptop:~/qemu/winxp$ sudo umount /dev/shm
Password:
umount: /dev/shm: not mounted
jrobinson@laptop:~/qemu/winxp$ sudo mount -t tmpfs -o size=272mb none /dev/shm
mount: wrong fs type, bad option, bad superblock on none,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

jrobinson@laptop:~/qemu/winxp$ 
```

What gives?

---

