---
title: "Why does this partition and only this one show up in thunar"
date: 2020-12-31
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2020-12-31
This one shows up in thunar as a drive:
```
/mnt/Scratch                              /home/chad/Desktop                   bind     x-systemd.requires=/home,x-systemd.requires=/mnt/Scratch,noatime,defaults,bind   0       0
```
I would like it to not show up as a removable drive/disk
```
$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system>                           <mount point>                        <type>   <options>                                                                        <dump>  <pass>
# / was on /dev/nvme0n1p2 during installation
UUID=43fff14c-8de1-4f07-b37e-333ff7d96675 /                                    ext4     noatime,discard,errors=remount-ro                                                0       1
# /home was on /dev/sdb2 during installation
UUID=b8362e2b-2cdb-40f4-a2a8-a9ed1207cb81 /home                                ext4     defaults                                                                         0       2
# /mnt/Home+ was on /dev/sda2 during installation
UUID=bf16e794-31f2-4fc4-93c4-44393c9b034e /mnt/Home+                           ext4     defaults                                                                         0       2
# /mnt/ISO was on /dev/sda4 during installation
UUID=85b4b658-8de3-4364-92d7-cd2ca4d85c47 /mnt/ISO                             ext4     defaults                                                                         0       2
# /mnt/VirtualBox was on /dev/sda3 during installation
UUID=68715821-36e4-4962-a583-a41115151dcd /mnt/VirtualBox                      ext4     defaults                                                                         0       2
# /tmp was moved to RAM after installation
tmpfs                                     /tmp                                 tmpfs    defaults,noatime,mode=1777                                                       0       0
# /media was moved to RAM after installation
tmpfs                                     /media                               tmpfs    defaults,size=1M,mode=755                                                        0       0
# /root was moved to /home/root after installation
/home/root                                /root                                bind     x-systemd.requires=/home,defaults,bind                                           0       0
# /var was moved to /dev/sdc1 after installation
UUID=3d1dd4e3-d423-4802-b52a-aa74d6fdc8bd /var                                 ext4     defaults                                                                         0       2
# swap was on /dev/sda5 during installation
UUID=f19176ad-6f15-434c-a987-d68e02067657 none                                 swap     sw                                                                               0       0
# /var/cache/apt/archives was moved tp /dev/sda1 after installation
UUID=bcbf1c29-de47-42e6-8f53-280358aceca0 /var/cache/apt/archives              ext4     x-systemd.requires=/var,defaults                                                 0       2
# UEFI Boot Partation
UUID=3F6C-6290                              /boot/efi                            vfat     defaults                                                                         0       1

# Scratch disk
UUID=f68d4e80-7a59-48ae-b2f9-afe841b65008 /mnt/Scratch                         ext4     defaults,noatime,discard                                                         0       2
/mnt/Scratch                              /home/chad/Desktop                   bind     x-systemd.requires=/home,x-systemd.requires=/mnt/Scratch,noatime,defaults,bind   0       0
# /mnt/Firefox/mozilla = /home/chad/.mozilla
UUID=c6cbd268-4bdd-4a96-ab35-fe76b9c3cae1 /mnt/Firefox                         ext4     defaults,noatime,discard                                                         0       2
/mnt/Firefox/mozilla                      /home/chad/.mozilla                  bind     x-systemd.requires=/home,x-systemd.requires=/mnt/Firefox,noatime,defaults,bind   0       0
# PS1 Squash File System
/home/chad/.emulationstation/ROM/psx.sqsh /home/chad/.emulationstation/ROM/psx squashfs x-systemd.requires=/home,loop                                                    0       0
```

---

### Post by LewisTM on 2021-01-01
I don't have Thunar installed so can't test this, but have you thought of simply mounting your Scratch disk directly as your Desktop directory without using a bind mount?
```
UUID=f68d4e80-7a59-48ae-b2f9-afe841b65008 /home/chad/Desktop                        ext4     defaults,noatime,discard                                                         0       2
```
You can mount disks in multiple places. Might help (or not).

Cheers

---

