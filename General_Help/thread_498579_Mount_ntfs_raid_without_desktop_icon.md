---
title: "Mount ntfs raid without desktop icon?"
date: 2007-07-11
forum: General Help
---

### Post by arsenic23 on 2007-07-11
Ok, I recently decided to mount my ntfs raid to my home folder with all my other partitions.  Everything worked spot on, but for some reason it placed an icon on my desktop.  This seems really odd to me since none of my other mounted partitions have this behavior.  I'd really appreciate it if someone could shed some light on this for me - I hate having non-temporary files on my desktop.

The offending fstab *(with username hidden)* :
```

proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=56cfa83b-68b0-4199-9aa2-b0d5df759c99 /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       /home/***/ext3     ext3    defaults        0       2
# /dev/sda6
UUID=52A4F450A4F437D5 /home/***/ntfs     ntfs    ro,user,users,uid=1000    0       0
# /dev/sda7
UUID=716d1b93-2479-496b-92ef-f7e9254b6fe3 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

/home/***/Games/broodwar.iso /mnt/starcraft  iso9660 ro,loop,auto    0       0
#/home/***/Games/puzzlefighter.iso    /mnt/puzzlefighter      iso9660 ro,loop,auto    0       0

/dev/mapper/sil_afbicccfdhej1   /home/***/win        ntfs    ro,user,users,uid=1000

```

---

### Post by merlinus on 2007-07-11
Alt-F2
gconf-editor
apps/Nautilus/desktop

Untick the various boxes for what you are not wanting to see.

-merlin

---

### Post by arsenic23 on 2007-07-11
Well, no, if I uncheck volumes_visible then I won't get my usb drives on my desktop when I plug them in, will I?

The thing is neigther of these place an icon on my desktop:
~/ext3
~/ntfs

But '~/win' does.  I though perhaps I had mounted it wrong, but could find little to no information on it by searching the forums or google.

---

