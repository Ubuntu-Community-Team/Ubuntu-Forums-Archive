---
title: "gksudo nautilus....doesn't allow working with all partitions"
date: 2008-04-22
forum: General Help
---

### Post by jeffsa12 on 2008-04-22
I've been using the gksudo nautilus command  or just sudo nautilus when I want to browse and make changes to a protected file with a text editor. 

I installed another HD to play with Vista, Vista Ultimate, and Sabayon. I want to get into Sabayons boot files from Ubuntu and cant seem to using nautilus with gksudo or sudo. When I click computer, it will only go back as far as Ubuntu root and not show all the HD's and partitions as it does in my user account. I put into the address bar of nautilus, computer:/// to replace the computer:/ that came up with the computer button......no luck.

In the past, I set up a Ubuntu root user account, but I want to get away from that. Is there a way to do what I'm trying using nautilus?


jeff@jeff-new-dsktp:~$ sudo fdisk -l
[sudo] password for jeff:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         393        6989    52990400    7  HPFS/NTFS
/dev/hda2               1         392     3148708+   b  W95 FAT32
/dev/hda3            6996       19457   100101015    f  W95 Ext'd (LBA)
/dev/hda5            6996        8955    15743668+   b  W95 FAT32
/dev/hda6            8956        9214     2080386   82  Linux swap / Solaris
/dev/hda7            9215       10141     7446096   83  Linux
/dev/hda8           10142       11068     7446096   83  Linux
/dev/hda9           11069       11995     7446096   83  Linux
/dev/hda10          11996       12922     7446096   83  Linux
/dev/hda11          12923       19457    52492356    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x71d4ff44

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb2   *           1        1313    10546641    7  HPFS/NTFS
/dev/hdb3            1314        9723    67553325    f  W95 Ext'd (LBA)
/dev/hdb5            1314        2376     8538516    b  W95 FAT32
/dev/hdb6            2377        2638     2104483+  82  Linux swap / Solaris
/dev/hdb7            2639        3565     7446096   83  Linux
/dev/hdb8            3566        9723    49464103+  83  Linux

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000543e6

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        5102    40981783+   7  HPFS/NTFS
/dev/hdd2            5103       10229    41182627+   7  HPFS/NTFS
/dev/hdd3           10230       19457    74123910    5  Extended
/dev/hdd5           10230       10486     2064321   82  Linux swap / Solaris
/dev/hdd6           10487       12398    15358108+  83  Linux
/dev/hdd7           12399       19457    56701386   83  Linux
jeff@jeff-new-dsktp:~$

---

### Post by jeffsa12 on 2008-04-22
Paying more attention to this issue today, I noticed after using and closing nautilus, the terminal I used to open it had the following message. It appears to be a permissions problem.

I had to use my root user account again......to copy Sabayons grub menu.lst and edit my Ubuntu's to boot into my new OS's.

jeff@jeff-new-dsktp:~$ gksudo nautilus
Initializing gnome-mount extension
Initializing nautilus-open-terminal extension
Initializing nautilus-share extension
Nautilus-Share-Message: REFRESHING SHARES
Nautilus-Share-Message: ------------------------------------------
Nautilus-Share-Message: spawn arg "net"
Nautilus-Share-Message: spawn arg "usershare"
Nautilus-Share-Message: spawn arg "info"
Nautilus-Share-Message: end of spawn args; SPAWNING

Nautilus-Share-Message: returned from spawn: SUCCESS: 
Nautilus-Share-Message: exit code 255
Nautilus-Share-Message: ------------------------------------------
Nautilus-Share-Message: **_Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: usershares are currently disabled_**

---

### Post by jeffsa12 on 2008-05-06
I figured this out.....

I have always use the "tree view" in the side panel when browing files with Nautilus. Switching it to "places" shows all drives and partitions. Just mount the ones you want to work with or view.

Now why this would be different from a regular user to gksudo user is what I'd like to konw.

---

