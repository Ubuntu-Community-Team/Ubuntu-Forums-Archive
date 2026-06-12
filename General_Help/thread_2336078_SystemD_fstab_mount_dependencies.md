---
title: "SystemD fstab mount dependencies"
date: 2016-09-04
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2016-09-04
I have had my boot fail cause of stuff not getting mounted[INDENT][https://ubuntuforums.org/showthread.php?t=2333121&p=13531165](https://ubuntuforums.org/showthread.php?t=2333121&p=13531165)
[/INDENT]
this was cause systemd mounts everything in parallel (how it even knows to mount /home after / idk, or even if it does at all as my /home has failed to mount)
i found a option i can use like [FONT=courier new]x-systemd.requires=/var[/FONT]
how do i use this to tell systemd to wait till [FONT=courier new]/var[/FONT] is mounted before trying to mount say [FONT=courier new]/var/cache/apt/archives[/FONT]

even if i can just set a propriety level eg:
[INDENT][FONT=courier new]/ would be 0
/home would be 1
/var would be 1
/tmp would be 1
/var/cache/apt/archives would be 2[/FONT]
[/INDENT]

---

### Post by pqwoerituytrueiwoq on 2016-09-04
For a few boots this seemed to work but still seems to not work
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system>                           <mount point>           <type>  <options>                           <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=5fbb664c-3d07-4801-b4e6-5a1ba1e01b93 /                       ext4    errors=remount-ro,noatime,discard   0       1
# /home was on /dev/sda2 during installation
UUID=98ef1e15-845e-4f01-b28a-8c8e00629b9b /home                   ext4    x-systemd.after=/                   0       2
# /var was on /dev/sda1 during installation
UUID=b8dfd4b4-a155-4932-9629-cfa5630891a4 /var                    ext4    x-systemd.after=/                   0       2
# /var/cache/apt/archives was on /dev/sda3 during installation
UUID=9b0788c7-d6e9-4db2-84e1-53400beb745b /var/cache/apt/archives ext4    x-systemd.after=/var                0       2
# swap was on /dev/sda4 during installation
UUID=a89bd850-d2e1-4486-b3e6-40b04fccb9c3 none                    swap    sw                                  0       0
# Move /tmp to ram to extenxd SSD Life
tmpfs                                     /tmp                    tmpfs   noatime,mode=1777,x-systemd.after=/ 0       0
# Move /media to ram to prevent clutter 
tmpfs                                     /media                  tmpfs   size=1M,mode=755,x-systemd.after=/  0       0
# Move Root to /home to get it off the SSD
/home/root                                /root                   none    bind,x-systemd.after=/home          0       0
```
Currently Testing this:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system>                           <mount point>           <type>  <options>                              <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=5fbb664c-3d07-4801-b4e6-5a1ba1e01b93 /                       ext4    errors=remount-ro,noatime,discard      0       1
# /home was on /dev/sda2 during installation
UUID=98ef1e15-845e-4f01-b28a-8c8e00629b9b /home                   ext4    x-systemd.requires=/                   0       2
# /var was on /dev/sda1 during installation
UUID=b8dfd4b4-a155-4932-9629-cfa5630891a4 /var                    ext4    x-systemd.requires=/                   0       2
# /var/cache/apt/archives was on /dev/sda3 during installation
UUID=9b0788c7-d6e9-4db2-84e1-53400beb745b /var/cache/apt/archives ext4    x-systemd.requires=/var                0       2
# swap was on /dev/sda4 during installation
UUID=a89bd850-d2e1-4486-b3e6-40b04fccb9c3 none                    swap    sw                                     0       0
# Move /tmp to ram to extenxd SSD Life
tmpfs                                     /tmp                    tmpfs   noatime,mode=1777,x-systemd.requires=/ 0       0
# Move /media to ram to prevent clutter
tmpfs                                     /media                  tmpfs   size=1M,mode=755,x-systemd.requires=/  0       0
# Move Root to /home to get it off the SSD
/home/root                                /root                   none    bind,x-systemd.requires=/home          0       0
```
but if this is what it takes to make it work how does a clean install only with a separate /home work?

---

