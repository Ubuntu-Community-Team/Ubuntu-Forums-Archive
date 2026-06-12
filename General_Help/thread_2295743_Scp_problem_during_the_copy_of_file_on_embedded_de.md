---
title: "Scp problem during the copy of file on embedded device"
date: 2015-09-21
forum: General Help
---

### Post by erotavlas on 2015-09-21
Hi,
I'm using the SSH protocol in order to copy files from my Ubuntu to an embedded device i.e. router. I'm using the standard syntax scp -v file.bin root@IP:/tmp/, but the  copying process arrives at about 95% and becomes stalled. Sometimes,  the percentage reaches the 100%, but if I try to connect via SSH to the device it is unreachable, but it responds to ping.
I have enough free space on the partition /tmp/ of the router about 6 MByte for the file about 4 MByte.

```

df -h
Filesystem                Size      Used Available Use% Mounted on
rootfs                  896.0K    212.0K    684.0K  24% /
/dev/root                 2.0M      2.0M         0 100% /rom
tmpfs                     6.4M     60.0K      6.4M   1% /tmp
tmpfs                   512.0K         0    512.0K   0% /dev
/dev/mtdblock4          896.0K    212.0K    684.0K  24% /overlay
overlayfs:/overlay      896.0K    212.0K    684.0K  24% /

```

While the RAM is quite full.

```

free
             total         used         free       shared      buffers
Mem:         13144        12268          876            0         1260
-/+ buffers:              11008         2136
Swap:            0            0            0

```

Do you have any hint?
Thank you

---

### Post by tgalati4 on 2015-09-21
Typically a temporary file is created when downloading, so you need twice the size of the file.  When the entire file is downloaded and checked, then it is copied to the final file destination.  It might work with 8 MB free.

You can try to force ssh Version 1 (-1) or use compression (-C) and set verbose (-v) so you can see the errors as they happen.

Unfortunately, linux does not behave when it is short of RAM and disk space.

The fact that you can't log in with ssh with a stalled copy is consistent with an out-of-space condition, since the ssh credentials for the session are stored in /tmp as well.

Try a fresh boot.  Remove any firewall policies, shared device descriptions, and anything else that would take up RAM and file space on the router.  Delete any extra files in /tmp including hidden files (except for your current .ssh session).  Make sure you have 8 MB free.  Then try your scp.

Otherwise, try shrinking the file that you are copying.

---

