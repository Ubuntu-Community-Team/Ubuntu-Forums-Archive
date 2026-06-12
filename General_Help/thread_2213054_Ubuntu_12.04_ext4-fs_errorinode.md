---
title: "Ubuntu 12.04 ext4-fs error/inode"
date: 2014-03-24
forum: General Help
---

### Post by john175 on 2014-03-24
[COLOR=#333333][FONT=UbuntuRegular]I am running a Dell PowerEdge T420 with Ubuntu 12.04 32bit. The hard drives are a RAID1 setup. Last week, I began getting errors that cause the build I am running to fail. I found this in the log file.
[/FONT][/COLOR]
[COLOR=#000000][[/COLOR][COLOR=#800000]970972.123632[/COLOR][COLOR=#000000]][/COLOR][COLOR=#000000] EXT4[/COLOR][COLOR=#000000]-[/COLOR][COLOR=#000000]fs error [/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]device sda1[/COLOR][COLOR=#000000]):[/COLOR][COLOR=#000000] ext4_ext_check_inode[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#800000]464[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#000000] inode [/COLOR][COLOR=#808080]#31202 702: comm python: bad header/extent: invalid extent entries - magic f30a, entries 1 , max 4(4), depth 0(0)[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]
[[/COLOR][COLOR=#800000]970972.123636[/COLOR][COLOR=#000000]][/COLOR][COLOR=#2B91AF]Aborting[/COLOR][COLOR=#000000] journal on device sda1[/COLOR][COLOR=#000000]-[/COLOR][COLOR=#800000]8.[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]
[[/COLOR][COLOR=#800000]970972.123681[/COLOR][COLOR=#000000]][/COLOR][COLOR=#000000] EXT4[/COLOR][COLOR=#000000]-[/COLOR][COLOR=#000000]fs [/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]sda1[/COLOR][COLOR=#000000]):[/COLOR][COLOR=#2B91AF]Remounting[/COLOR][COLOR=#000000] filesystem read[/COLOR][COLOR=#000000]-[/COLOR][COLOR=#000000]only
[/COLOR][COLOR=#333333][FONT=UbuntuRegular]
I have run fsck on boot, it seems to find errors and correct them but the issue repeats if I kick off a new build. I have also booted from a live CD and run e2fsck -ccfkp. That completes and indicates it updated bad block inode. Issue repeats if I start a new build. The inode #31202 is the same every time.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Any ideas on where to start troubleshooting?[/FONT][/COLOR]

---

