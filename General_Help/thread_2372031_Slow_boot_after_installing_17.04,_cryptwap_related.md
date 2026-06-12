---
title: "Slow boot after installing 17.04, cryptwap related"
date: 2017-09-20
forum: General Help
---

### Post by tzeny on 2017-09-20
Today I reinstalled Windows 10 and alongside it Ubuntu 17.04. Both systems are installed on their own SSDs. Everything went smoothly, I checked to make sure I could boot into both of them but I have an issue.

Whenever I start Ubuntu, it takes a long time to pass the loading screen. After checking /var/log/boot.log I found this:
```
/dev/sdb1: clean, 223382/7815168 files, 2408734/31258368 blocks
[  *** ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (30s /[   ***] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (30s /[    **] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[     *] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[    **] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[   ***] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (32s /[  *** ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (33s /[ ***  ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (33s /[***   ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[**    ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[*     ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[**    ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (35s /[***   ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (36s /[ ***  ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (36s /[  *** ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[   ***] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[    **] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[     *] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (38s /[    **] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (39s /[   ***] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (39s /[  *** ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[ ***  ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[***   ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[**    ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (41s /[*     ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (42s /[**    ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (42s /[***   ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[ ***  ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[  *** ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[   ***] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (44s /[    **] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (45s /[     *] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (45s /[    **] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[   ***] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[  *** ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[ ***  ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (47s /[***   ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (48s /[**    ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (48s /[*     ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[**    ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[***   ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[ ***  ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (50s /[  *** ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (51s /[   ***] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (51s /[    **] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[     *] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[    **] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[   ***] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (53s /[  *** ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (54s /[ ***  ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (54s /[***   ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[**    ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[*     ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[**    ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (56s /[***   ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (57s /[ ***  ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (57s /[  *** ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[   ***] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[    **] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[     *] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (59s /[    **] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [   ***] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [  *** ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[ ***  ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[***   ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[**    ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [*     ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [**    ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [***   ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[ ***  ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[  *** ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[   ***] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [    **] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [     *] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [    **] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[   ***] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[  *** ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[ ***  ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [***   ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [**    ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [*     ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[**    ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[***   ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[ ***  ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [  *** ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [   ***] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [    **] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[     *] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[    **] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[   ***] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [  *** ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [ ***  ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [***   ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[**    ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[*     ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[**    ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [***   ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [ ***  ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [  *** ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[   ***] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[    **] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[     *] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [    **] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [   ***] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [  *** ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[ ***  ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[***   ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[**    ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [*     ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [**    ] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [***   ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[ ***  ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[  *** ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[   ***] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [    **] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [     *] (2 of 2) A start job is running for dev-mapper-cryptswap1.device (1min [    **] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[   ***] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[  *** ] (1 of 2) A start job is running for dev-disk-by\x2duuid-\x5cx2fswapfile[ TIME ] Timed out waiting for device dev-disk-by\x2duuid-\x5cx2fswapfile.device.
[DEPEND] Dependency failed for Cryptography Setup for cryptswap1.
[DEPEND] Dependency failed for Encrypted Volumes.
[DEPEND] Dependency failed for dev-mapper-cryptswap1.device.
[DEPEND] Dependency failed for /dev/mapper/cryptswap1.
[DEPEND] Dependency failed for Swap.
[  OK  ] Reached target System Initialization.

```

After a bit of digging online, I found that I had no swapfile, and created one at /swapfile.
I checked it's existence by using swapon --show
```
NAME      TYPE SIZE USED PRIO
/swapfile file   2G   0B   -1
```

This is my /etc/fstab:
```
# / was on /dev/sdb1 during installation
UUID=e9b7de64-4bfc-4a89-b694-052fce863563 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=EA8E-157F  /boot/efi       vfat    umask=0077      0       1
/swapfile none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```

This is my /etc/crypttab
```
cryptswap1 UUID=/swapfile /dev/urandom swap,offset=1024,cipher=aes-xts-plain64
```

Do you have any idea how to fix this?

---

### Post by tzeny on 2017-09-20
I figured out the fix:

First follow the instructions here to create a swap file: [http://linuxbsdos.com/2017/05/26/replace-the-swap-partition-with-a-swap-file-after-upgrading-to-ubuntu-17-04/](http://linuxbsdos.com/2017/05/26/replace-the-swap-partition-with-a-swap-file-after-upgrading-to-ubuntu-17-04/)

Next edit /etc/crypttab:
```
cryptswap1 /swapfile /dev/urandom swap,offset=1024,cipher=aes-xts-plain64
```

Be sure not to add UUID in there.

---

### Post by ajgreeny on 2017-09-21
Great news! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

