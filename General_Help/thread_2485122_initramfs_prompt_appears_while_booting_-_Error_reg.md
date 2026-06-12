---
title: "initramfs prompt appears while booting - Error regarding zfs mountpoint"
date: 2023-03-20
forum: General Help
---

### Post by weeru on 2023-03-20
[COLOR=#232629][FONT=-apple-system]I am getting the following error if i try to boot my system:[/FONT][/COLOR]
```
Busybox v1.30.1
Gave up waiting for root file system device. Common problems:
- Boot args (cat /proc/cmdline
    - Check rootdelay= (did the system wait long enough?
- Missing modules (cat /proc/modules; ls dev
ALERT! ZFS=rpool/ROOT/ubuntu does not exist. Dropping to a shell! 
```
[COLOR=#232629][FONT=-apple-system]I've booted from a live system and according to **other-locations:///**, the mountpoint **rpool** does exist. But i cant reach the point via terminal (/media/ubuntu is empty).[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]If i just doubleclick the mointpoint, which is listed via **other-locations:///**, i get the following error:[/FONT][/COLOR][INDENT][FONT=inherit]"Error mounting /dev/nvme0 at /media/ubuntu/rpool: unknown filesystem type zfs_member"[/FONT]
[/INDENT]
[COLOR=#232629][FONT=-apple-system]Thank you for your help in advance


Edit:
SOLVED! In my case, there only was the way to recover the system by recovery mode.[/FONT][/COLOR]

---

