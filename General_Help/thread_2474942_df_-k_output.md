---
title: "df -k output"
date: 2022-05-12
forum: General Help
---

### Post by cam17 on 2022-05-12
I noticed allot of /dev/loopxx when I run df -k, Is that normal ?

df -k
```
Filesystem     1K-blocks     Used Available Use% Mounted on
udev             8097544        0   8097544   0% /dev
tmpfs            1626556     2312   1624244   1% /run
/dev/nvme0n1p5  95792540 81516300   9367184  90% /
tmpfs            8132764        0   8132764   0% /dev/shm
tmpfs               5120        4      5116   1% /run/lock
tmpfs            8132764        0   8132764   0% /sys/fs/cgroup
/dev/loop0           128      128         0 100% /snap/bare/5
/dev/loop2        259712   259712         0 100% /snap/brave/159
/dev/loop3         63488    63488         0 100% /snap/core20/1434
/dev/loop4         56960    56960         0 100% /snap/core18/2344
/dev/loop5         63488    63488         0 100% /snap/core20/1405
/dev/loop6         52224    52224         0 100% /snap/snap-store/547
/dev/loop7         66816    66816         0 100% /snap/gtk-common-themes/1519
/dev/loop8        434432   434432         0 100% /snap/kde-frameworks-5-91-qt-5-15-3-core20/1
/dev/loop9         45824    45824         0 100% /snap/snapd/15534
/dev/loop10       224256   224256         0 100% /snap/gnome-3-34-1804/72
/dev/loop11         2560     2560         0 100% /snap/gnome-clocks/446
/dev/loop12        86528    86528         0 100% /snap/wire/237
/dev/loop13       254848   254848         0 100% /snap/gnome-3-38-2004/99
/dev/loop14        21120    21120         0 100% /snap/keepassxc/1563
/dev/loop15       638720   638720         0 100% /snap/freecad/22
/dev/loop16        44800    44800         0 100% /snap/snapd/15177
/dev/loop17       153216   153216         0 100% /snap/joplin-desktop/27
/dev/loop18       253952   253952         0 100% /snap/gnome-3-38-2004/87
/dev/loop19       477056   477056         0 100% /snap/onionshare/15
/dev/loop20        56960    56960         0 100% /snap/core18/2284
/dev/loop21       168832   168832         0 100% /snap/gnome-3-28-1804/161
/dev/loop22       302848   302848         0 100% /snap/vlc/2344
/dev/loop23        55552    55552         0 100% /snap/snap-store/558
/dev/loop24       640384   640384         0 100% /snap/libreoffice/247
/dev/loop25       434432   434432         0 100% /snap/kde-frameworks-5-qt-5-15-3-core20/8
/dev/loop26        66688    66688         0 100% /snap/gtk-common-themes/1515
/dev/loop27       224256   224256         0 100% /snap/gnome-3-34-1804/77
/dev/loop28       192256   192256         0 100% /snap/deja-dup/520
/dev/loop29       153216   153216         0 100% /snap/joplin-desktop/26
/dev/loop30       272640   272640         0 100% /snap/kalzium/59
/dev/loop31       640640   640640         0 100% /snap/libreoffice/250
/dev/loop32        21120    21120         0 100% /snap/keepassxc/1552
/dev/loop33          256      256         0 100% /snap/kmag/67
/dev/nvme0n1p1    262144    35080    227064  14% /boot/efi
tmpfs            1626552      124   1626428   1% /run/user/1000
/dev/loop34       259712   259712         0 100% /snap/brave/160
```

---

### Post by Bashing-om on 2022-05-12
cam17 - hello

> 
Is that normal ?


It is; as you appear to have a lot of snap apps installed :D

[INDENT]the kernel keeps track of what is
[/INDENT]

---

### Post by cam17 on 2022-05-12
Thanks

---

