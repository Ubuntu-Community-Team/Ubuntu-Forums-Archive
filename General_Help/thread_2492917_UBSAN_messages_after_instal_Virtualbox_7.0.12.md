---
title: "UBSAN messages after instal Virtualbox 7.0.12"
date: 2023-11-27
forum: General Help
---

### Post by rodride on 2023-11-27
Hi,
[I]I am running Ubutu 22.04 with gnome-shell 42.1. After intalling Virtualbox 7.0.12, i have UBSAN messages on each reboot :
```

17:23:26 kernel: index 344 is out of range for type 'uint32_t [1]'
17:23:26 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/common/log/log.c:4161:34
17:23:26 kernel: ================================================================================
17:23:26 kernel: index 344 is out of range for type 'uint32_t [1]'
17:23:26 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/common/log/log.c:551:41
17:23:26 kernel: ================================================================================
17:23:25 kernel: index 2 is out of range for type 'SUPGIPCPU [1]'
17:23:25 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/SUPDrvGip.c:3997:53
17:23:25 kernel: ================================================================================
17:23:25 kernel: index 2 is out of range for type 'SUPGIPCPU [1]'
17:23:25 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/SUPDrvGip.c:4274:52
17:23:25 kernel: ================================================================================
17:23:25 kernel: index 3 is out of range for type 'SUPGIPCPU [1]'
17:23:25 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/SUPDrvGip.c:4041:33
17:23:25 kernel: ================================================================================
17:23:25 kernel: index 1 is out of range for type 'SUPGIPCPU [1]'
17:23:25 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/SUPDrvGip.c:180:24
17:23:25 kernel: ================================================================================
17:23:25 kernel: index 3 is out of range for type 'SUPGIPCPU [1]'
17:23:25 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/SUPDrvGip.c:4253:33
17:23:25 kernel: ================================================================================
17:23:25 kernel: index 3 is out of range for type 'SUPGIPCPU [1]'
17:23:25 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/SUPDrvGip.c:4206:46
17:23:25 kernel: ================================================================================
17:23:25 kernel: index 2 is out of range for type 'SUPGIPCPU [1]'
17:23:25 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/SUPDrvGip.c:4169:42
17:23:25 kernel: ================================================================================
17:23:25 kernel: index 2 is out of range for type 'SUPGIPCPU [1]'
17:23:25 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/SUPDrvGip.c:1457:40
17:23:25 kernel: ================================================================================
17:23:25 kernel: index 1 is out of range for type 'SUPGIPCPU [1]'
17:23:25 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/SUPDrvGip.c:1491:5
17:23:25 kernel: ================================================================================
17:23:25 kernel: index 1 is out of range for type 'SUPGIPCPU [1]'
17:23:25 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/SUPDrvGip.c:1465:16
17:23:25 kernel: ================================================================================
17:23:25 kernel: index 1 is out of range for type 'SUPGIPCPU [1]'
17:23:25 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/SUPDrvGip.c:1464:16
17:23:25 kernel: ================================================================================
17:23:25 kernel: index 1 is out of range for type 'SUPGIPCPU [1]'
17:23:25 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/SUPDrvGip.c:1462:5
17:23:25 kernel: ================================================================================
17:23:25 kernel: index 1 is out of range for type 'SUPGIPCPU [1]'
17:23:25 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/SUPDrvGip.c:1461:35
17:23:25 kernel: ================================================================================
17:23:25 kernel: index 1 is out of range for type 'SUPGIPCPU [1]'
17:23:25 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/SUPDrvGip.c:1460:35
17:23:25 kernel: ================================================================================
17:23:25 kernel: index 1 is out of range for type 'SUPGIPCPU [1]'
17:23:25 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/SUPDrvGip.c:1401:13
17:23:25 kernel: ================================================================================
17:23:25 kernel: index 1 is out of range for type 'SUPGIPCPU [1]'
17:23:25 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/SUPDrvGip.c:1392:24
17:23:25 kernel: ================================================================================
17:23:25 kernel: index 1 is out of range for type 'SUPGIPCPU [1]'
17:23:25 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/SUPDrvGip.c:904:43
17:23:25 kernel: ================================================================================
17:23:25 kernel: index 2 is out of range for type 'SUPGIPCPU [1]'
17:23:25 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/SUPDrvGip.c:1956:44
17:23:25 kernel: ================================================================================
17:23:25 kernel: index 3 is out of range for type 'page *[1]'
17:23:25 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/r0drv/linux/memobj-r0drv-linux.c:596:45
17:23:25 kernel: ================================================================================
17:23:25 kernel: index 1 is out of range for type 'page *[1]'
17:23:25 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/r0drv/linux/memobj-r0drv-linux.c:399:33
17:23:25 kernel: ================================================================================
17:23:25 kernel: index 1 is out of range for type 'uint32_t [1]'
17:23:25 kernel: UBSAN: array-index-out-of-bounds in /tmp/vbox.0/common/log/log.c:1791:41
17:23:25 kernel: ================================================================================

```

What do they mean, are they serious and can they be removed? In addition, I can no longer open a session on my real time kernel.
[/I]
Any ideas please ?

---

