---
title: "periferals on wubi installation"
date: 2008-05-20
forum: General Help
---

### Post by catonano on 2008-05-20
Hello people,

I installed 8.04 the wubi way, great, I have to say.

BUT I'd like to understand what disks does the system sees and how they are mapped onto the filesystem.

In windows I had 2 partitions, C: and D:, on the same disk and they are FAT32.

The wubi files are on D:

Inside Ubuntu I see a /media/disk which is mapped to C: and /host which is mapped to D:

I type "mount" in the terminal and I find /media/disk in the output but NOT /host.

Why ?

Look:

adriano@adriano-laptop:~$ mount | grep /host
/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
adriano@adriano-laptop:~$ 

There are the root filesystem mounted on / and that's ok. Then, there's the one mounted on /boot and that's ok too. BUT there's nothing mounted on /host, as I expected.

Further, if I type "cat /proc/mounts", then I find /host ! Look :

adriano@adriano-laptop:~$ cat /proc/mounts | grep /host
/dev/disk/by-uuid/3073-1408 /host vfat rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1 0 0

there it is. It's weird it's identified by the uuid 3073.1408 but at least there's something of type vfat mounted on /host.

Why are the contents of /proc/mounts and the output of mount different ?

What's going on ? 

Thanks for any hint
Bye
Catonano

---

### Post by ago on 2008-05-20
/host is treated in a special way because it hosts root. So, for instance, it cannot be unmounted.

You can see it in 

cat /proc/mounts

---

