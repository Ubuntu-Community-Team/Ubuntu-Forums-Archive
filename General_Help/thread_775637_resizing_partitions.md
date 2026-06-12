---
title: "resizing partitions?"
date: 2008-04-30
forum: General Help
---

### Post by MemoryDump on 2008-04-30
hey all,

I'm wondering if this is possible to do: (easily)

I'd like to resize 2 existing partitions.. both ext3.

I'd like to shrink my "/" partition and add the free space to my "/home" partition. Can this be done?

Here's my df -h:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              64G  3.6G   57G   6% /
varrun               1008M  244K 1007M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
procbususb           1008M   56K 1007M   1% /proc/bus/usb
udev                 1008M   56K 1007M   1% /dev
devshm               1008M   52K 1007M   1% /dev/shm
lrm                  1008M   38M  970M   4% /lib/modules/2.6.24-16-rt/volatile
/dev/sda1              82G   40G   38G  52% /home
gvfs-fuse-daemon       64G  3.6G   57G   6% /home/memdmp/.gvfs

```

thanks
-MD

---

### Post by ryanhaigh on 2008-04-30
Unfortunately this won't be that simple because even after resizing the partitions the UUID will have changed which means you will need to modify grub, fstab and initramfs. There are definately posts on these forums explaining how to do these things.

Apart from that it seems as though sda2 is not shown and is obviously between the partitions you want to resize. If this is swap that is less of an issue. You could delete the swap partition, resize / to desired, recreate the swap and then expand /home to fill the leftover space.

---

