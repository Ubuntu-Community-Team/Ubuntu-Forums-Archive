---
title: "Mount --bind ZFS at boot"
date: 2013-11-03
forum: General Help
---

### Post by thebuckstops on 2013-11-03
[SIZE=2][FONT=verdana]Hi all,

Some help required. I currently have a headless version of 13.10 running on my NAS, with SFTP set up such that specific users logging in remotely are chrooted to their home directory. However, I also want them to be able to read the communal data storage areas that are stored on the same server in a ZFS file system, mounted at /mnt/data. Symlinks obviously don't work, as the chrooting prevents them. The only workaround I've found is:
[FONT=courier new]sudo mount --bind /mnt/data/tv /home/user/tv[/FONT]

This is fine, but obviously not persistent over reboots. My ZFS doesn't show up when using [FONT=courier new]blkid[/FONT], and I know the ZFSoL drivers don't use fstab to mount - so I've no real idea how/when to automate the mounting. My current thinking is:
1) create script [FONT=courier new]mount-bind.sh[/FONT] in /home/colin/scripts
```
[COLOR=#000000]#!/bin/sh[/COLOR]
[COLOR=#000000]mount --bind /mnt/data/tv /home/user/tv[/COLOR]
```[/FONT][/SIZE][FONT=courier new][FONT=arial][SIZE=2][FONT=verdana]
2) [FONT=courier new]ln -s /home/colin/scripts/mount-bind.sh /etc/init.d/mount-bind[/FONT]
3) [FONT=courier new]chmod +x /home/colin/scripts/mount-bind.sh[/FONT]
3) [FONT=courier new]update-rc.d mount-bind.sh defaults[/FONT][SIZE=2]

So, first question - will this work? Second question - even if yes, is this the best/most elegant/most appropriate/most sensible route to achieving my goal[/SIZE]

Thanks in anticipation of the help...
[/FONT][/SIZE]
[/FONT][/FONT]

---

