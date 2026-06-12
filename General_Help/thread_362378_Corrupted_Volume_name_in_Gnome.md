---
title: "Corrupted Volume name in Gnome"
date: 2007-02-15
forum: General Help
---

### Post by AmazingRando on 2007-02-15
Hi everyone-

I was wondering if you could give me an idea about this problem.  One of my partitions, which is a FAT32 partition that I use when I need to run Windows, has the volume name of "trol\Sessio" and I can't change it. Any thoughts on why this happened, and more importantly, how I fix it? :confused: 

AR

[IMG]http://www.makatea.com/Screenshot.png[/IMG]

---

### Post by mssever on 2007-02-15
That's set in /etc/fstab and the mount point. See [How to fstab]("http://ubuntuforums.org/showthread.php?t=283131").

---

### Post by budgie9 on 2007-02-15
You may find as I did a couple of weeks back, (search on my name) that the fstab is set correctly and you will still not be able to correct the naming problem.
The only way I could correct the name was to format the partition, in my case, in XP and leave the name section blank when doing so. I discovered it was not Ubuntu causing the problem but XP.

---

### Post by dcstar on 2007-02-15
> **budgie9 said:**
> You may find as I did a couple of weeks back, (search on my name) that the fstab is set correctly and you will still not be able to correct the naming problem.
The only way I could correct the name was to format the partition, in my case, in XP and leave the name section blank when doing so. I discovered it was not Ubuntu causing the problem but XP.

There is a command to change the label of a DOS partition, **mkdosfs** (I think.....) has an option for this.
```
man -k dos
``` will list the right one (but I'm not sure if it will keep the existing data intact........)

---

### Post by mssever on 2007-02-16
So you're saying it's likely a problem with the partition's label? If that's the case, you can correct it in Windows as you suggested, but you can also fix it in Linux. The how to fstab post I linked to above has detailed info on this, as well.

---

### Post by VuDu on 2007-02-17
Hi there, the same happened to me today when installing edgy right after installing windows XP.
I'm not sure but this seems to be a issue with edgy, since the volume names seem to make some sence.
In his case "trol\Sessio" might stand for a path of something like Control \ Sessions. Mine is "ateImageWit" wich seems something about some Image With... maybe.
So.. something seems to be copying some random text and using it as a volume label.

When I uses the Walkthough you pointed, mlabel said the volume had no label... just in case, I set one and then removed it.


```

vudu@vudumachine:~$ ls /dev/disk/by-id -lah
total 0
drwxr-xr-x 2 root root 180 2007-02-17 01:23 .
drwxr-xr-x 6 root root 120 2007-02-17 01:23 ..
lrwxrwxrwx 1 root root   9 2007-02-17 01:23 ata-FUJITSU_MHV2060AT_NS82T592696B -> ../../hda
lrwxrwxrwx 1 root root  10 2007-02-17 01:23 ata-FUJITSU_MHV2060AT_NS82T592696B-part1 -> ../../hda1
lrwxrwxrwx 1 root root  10 2007-02-17 01:23 ata-FUJITSU_MHV2060AT_NS82T592696B-part2 -> ../../hda2
lrwxrwxrwx 1 root root  10 2007-02-17 01:23 ata-FUJITSU_MHV2060AT_NS82T592696B-part3 -> ../../hda3
lrwxrwxrwx 1 root root  10 2007-02-17 01:23 ata-FUJITSU_MHV2060AT_NS82T592696B-part4 -> ../../hda4
lrwxrwxrwx 1 root root  10 2007-02-17 01:23 ata-FUJITSU_MHV2060AT_NS82T592696B-part5 -> ../../hda5
lrwxrwxrwx 1 root root   9 2007-02-17 01:23 ata-TOSHIBA_CDDVDW_SDR6472U_0000170233 -> ../../hdb

```

```
vudu@vudumachine:~$ ls /dev/disk/by-label -lah
total 0
drwxr-xr-x 2 root root  60 2007-02-17 01:23 .
drwxr-xr-x 6 root root 120 2007-02-17 01:23 ..
lrwxrwxrwx 1 root root  10 2007-02-17 01:23 ateImageWit -> ../../hda1

```

hda1 -> fat32 WindowsXP
hda2 -> Ubuntu 6.10
hda3 -> Swap
hda4 -> extended
hda5 -> big fat32 partitions


EDIT:
That still didn't work so I followed this: [http://www.ubuntuforums.org/showthread.php?t=70741&highlight=volume.policy.desired_mount_point](http://www.ubuntuforums.org/showthread.php?t=70741&highlight=volume.policy.desired_mount_point) and now everything is working ok ;)

---

