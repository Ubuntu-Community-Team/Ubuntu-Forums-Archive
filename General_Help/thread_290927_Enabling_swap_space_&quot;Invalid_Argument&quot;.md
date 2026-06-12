---
title: "Enabling swap space: &quot;Invalid Argument&quot;"
date: 2006-11-01
forum: General Help
---

### Post by kristopher.reed on 2006-11-01
I am running Ubuntu Edgy on my computer, and as of a few days ago I noticed that my swap space was not being used. It is always at zero (the "top" command says "0k total, 0k used, 0k free). I tried turning the swap space on--I am only assuming that it is not on, but I don't know how to check this--using the command "swapon -a", but that gives me the error message "swapon: /dev/disk/by-uuid/45cde543-73e7-480b-95cf-b982b44035b4: Invalid argument"

I also tried "swapon -U 45cde543-73e7-480b-95cf-b982b44035b4" but I recieved the same error message.

I modified my /etc/fstab config file from this:
[other stuff]
# /dev/sda2 -- converted during upgrade to edgy
UUID=45cde543-73e7-480b-95cf-b982b44035b4 none swap sw 0 0
[other stuff]

And changed it to this:
[other stuff]
# /dev/sda2 -- converted during upgrade to edgy
#UUID=45cde543-73e7-480b-95cf-b982b44035b4 none swap sw 0 0
/dev/sda2 none swap sw 0 0
[other stuff]

A "swapon -a" only yields this message: "swapon: /dev/sda2: Invalid argument"

And in case it is needed, here is what my disk looks like (from fdisk):
/dev/sda1   *           1        1542    12386083+   7  HPFS/NTFS
/dev/sda2            1543        1736     1558305   82  Linux swap / Solaris
/dev/sda3            1737        2379     5164897+   c  W95 FAT32 (LBA)
/dev/sda4            2380        7272    39303022+  83  Linux

And here is the output from "vol_id /dev/sda2":
ID_FS_USAGE=other
ID_FS_TYPE=swsusp
ID_FS_VERSION=2
ID_FS_UUID=45cde543-73e7-480b-95cf-b982b44035b4
ID_FS_LABEL=
ID_FS_LABEL_SAFE=

I really don't know what I should do now, or even what is wrong. Any help would be appreciated.

Thank you in advance.

~Kris

---

### Post by lzap on 2006-12-06
> **kristopher.reed said:**
> I am running Ubuntu Edgy on my computer, and as of a few days ago I noticed that my swap space was not being used. It is always at zero (the "top" command says "0k total, 0k used, 0k free). I tried turning the swap space on--I am only assuming that it is not on, but I don't know how to check this--using the command "swapon -a", but that gives me the error message "swapon: /dev/disk/by-uuid/45cde543-73e7-480b-95cf-b982b44035b4: Invalid argument"


root@teevee:/dev/disk/by-uuid# mkswap /dev/hdd2
Setting up swapspace version 1, size = 723820 kB
no label, UUID=14d13bca-d7d5-4518-bebe-b0e39305e844

root@teevee:/dev/disk/by-uuid# swapon /dev/hdd2

now go to fstab and change the UUID of your swap line to the new one (see above)

---

