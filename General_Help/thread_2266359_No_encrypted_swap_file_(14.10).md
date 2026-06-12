---
title: "No encrypted swap file (14.10)"
date: 2015-02-22
forum: General Help
---

### Post by Popkultur on 2015-02-22
Hello,

I have issues with my encrypted swapfile.

fdisk -l says
```

Disk /dev/sda: 20 GiB, 21474836480 bytes, 41943040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x4eb68bbc

Device     Boot  Start      End  Sectors  Size Id Type
/dev/sda1  *      2048   499711   497664  243M 83 Linux
/dev/sda2       501758 41940991 41439234 19,8G  5 Extended
/dev/sda5       501760 41940991 41439232 19,8G 83 Linux

```

swapon -summary says
```

Filename                Type        Size    Used    Priority
/dev/dm-2                                  partition    1044476    0    -1

```

vi fstab says
```

/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=97904678-e377-4d46-b889-5298a4b3c938 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```

vi crypttab says
```

sda5_crypt UUID=6dbbcd39-c952-4c7b-b86e-85841ba24608 none luks,discard
cryptswap1 UUID=e812691c-a89c-4ba8-9764-89e2bd2d4021 /dev/urandom swap,cipher=aes-cbc-essiv:sha256

```

what to do about this? Every time I boot, it says “Disk drive for dev/mapper/cryptswap1 is not ready”

---

### Post by HermanAB on 2015-02-22
Howdy,

You should read the swapon man page.  Everything is in there.

---

