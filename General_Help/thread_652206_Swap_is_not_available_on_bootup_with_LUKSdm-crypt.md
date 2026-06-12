---
title: "Swap is not available on bootup with LUKS/dm-crypt"
date: 2007-12-28
forum: General Help
---

### Post by tdn on 2007-12-28
I use LUKS and dm-crypt to encrypt both my root file system and swap.
For some reason swap will not work after boot.
 Every time the machine has booted, the swap is not enabled.
I have a log below that illustrates the problem. (the log is also available in a more readable format here: [http://thomasdamgaard.dk/paste/P1027.html](http://thomasdamgaard.dk/paste/P1027.html))
I hope you can help me to get swap to work even with reboot, as it is very annoying that I have to go through the process shown below after each reboot.
 Note: I run Ubuntu Feisty.
(tdn@bart) (07-12-10 20:21) (P:0 L:1) [0 [ 20:21:21 up 4:52, 1 user, load average: 1.94, 2.30, 2.55]
 ~ $ free
              total used free shared buffers cached
 Mem: 2075556 1763636 311920 0 30200 1023092
 -/+ buffers/cache: 710344 1365212
 Swap: 0 0 0
 (tdn@bart) (07-12-10 20:21) (P:0 L:1) [0 [ 20:21:21 up 4:52, 1 user, load average: 1.94, 2.30, 2.55]
 ~ $ sudo cryptsetup luksOpen --key-file /root/luks-key-files/cswap /dev/sda3 cswap
 Password:
 key slot 0 unlocked.
 Command successful.
 (tdn@bart) (07-12-10 20:21) (P:0 L:1) [0 [ 20:21:36 up 4:52, 1 user, load average: 1.74, 2.24, 2.52]
 ~ $ sudo swapon /dev/mapper/cswap
 (tdn@bart) (07-12-10 20:21) (P:0 L:1) [0 [ 20:21:42 up 4:52, 1 user, load average: 1.77, 2.23, 2.51]
 ~ $ free
              total used free shared buffers cached
 Mem: 2075556 1768660 306896 0 30468 1025588
 -/+ buffers/cache: 712604 1362952
 Swap: 4240636 0 4240636
 (tdn@bart) (07-12-10 20:21) (P:0 L:1) [0 [ 20:21:46 up 4:53, 1 user, load average: 1.77, 2.23, 2.51]
 ~ $ cat /etc/crypttab
 # <target name> <source device> <key file> <options>
 root /dev/sda2 none cipher=aes-cbc-essiv:sha256
 #cswap /dev/sda3 /dev/urandom swap
 cswap /dev/sda3 /root/luks-key-files/cswap swap
 #cswap /dev/sda3 none swap
 #root /dev/sdb2 none cipher=aes-cbc-essiv:sha256
 #cswap /dev/sdb3 /dev/urandom swap
 (tdn@bart) (07-12-10 20:21) (P:0 L:1) [0 [ 20:21:52 up 4:53, 1 user, load average: 1.90, 2.24, 2.51]
 ~ $ /etc
 (tdn@bart) (07-12-10 20:22) (P:0 L:1) [1 [ 20:22:04 up 4:53, 1 user, load average: 1.60, 2.16, 2.49]
 ~ $ cat /etc/fstab
 # /etc/fstab: static file system information.
 #
 # <file system> <mount point> <type> <options> <dump> <pass>
 proc /proc proc defaults 0 0
 # /dev/sda6
 #UUID=c7045f36-d8be-4ef3-8585-e9d7d41b540 / ext3 defaults,errors=remount-ro 0 1
 # /dev/mapper/root
 #UUID=09712129-a956-48ce-810d-9b7bd6bd2178 / ext3 defaults,errors=remount-ro 0 1
 /dev/mapper/root / ext3 defaults,errors=remount-ro 0 1
 # /dev/sda2
 UUID=8c68bf3a-ebd9-4fac-aab5-c7ae61ae5e9a /boot ext3 defaults 0 2
 # /dev/sda1
 #UUID=80C2F69090FA0800 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
 # /dev/sda4
 #UUID=1B33-0A00 /media/sda4 vfat defaults,utf8,umask=007,gid=46 0 1
 /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
 /dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
 /dev/mapper/cswap none swap sw 0 0
 (tdn@bart) (07-12-10 20:22) (P:0 L:1) [0 [ 20:22:08 up 4:53, 1 user, load average: 1.72, 2.18, 2.49]
 ~ $

---

