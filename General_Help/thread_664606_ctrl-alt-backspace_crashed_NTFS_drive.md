---
title: "ctrl-alt-backspace crashed NTFS drive"
date: 2008-01-11
forum: General Help
---

### Post by descentspb on 2008-01-11
The message itself is in the header. Is there a way just to restart X, without sudden unmounting of the drives.

I know it was my mistake to do this without unmounting the drives, but why does ubuntu unmount the drives if i just want to restart the videodisplay? Is there any workaround to it?

---

### Post by taurus on 2008-01-11
I guess you mount your ntfs partition when you log in.  And when you restart X, you will be logged out so basically the drive would be unmounted to.  If you want it to mount each time you boot Ubuntu, why not add an entry in /etc/fstab so you don't have to worry about mount and unmount it.

What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by descentspb on 2008-01-12
No problem, sorry for the output in russian, but basically, i think you'll get it.

descent@descent:~$ sudo fdisk -l

&#1044;&#1080;&#1089;&#1082; /dev/sda: 160.0 &#1043;&#1041;, 160041885696 &#1073;&#1072;&#1081;&#1090;
255 heads, 63 sectors/track, 19457 cylinders
Units = &#1094;&#1080;&#1083;&#1080;&#1085;&#1076;&#1088;&#1099; of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8a7c8a7

&#1059;&#1089;&#1090;&#1088;-&#1074;&#1086; &#1047;&#1072;&#1075;&#1088;     &#1053;&#1072;&#1095;&#1072;&#1083;&#1086;       &#1050;&#1086;&#1085;&#1077;&#1094;       &#1041;&#1083;&#1086;&#1082;&#1080;   Id  &#1057;&#1080;&#1089;&#1090;&#1077;&#1084;&#1072;
/dev/sda1   *           1         319     2562336    b  W95 FAT32
/dev/sda2             320       19457   153725985    5  &#1056;&#1072;&#1089;&#1096;&#1080;&#1088;&#1077;&#1085;&#1085;&#1099;&#1081;
/dev/sda5            4206       19457   122511658+   7  HPFS/NTFS
/dev/sda6             320         381      497952   82  Linux &#1089;&#1074;&#1086;&#1087; / Solaris
/dev/sda7             382        4205    30716248+  83  Linux

&#1055;&#1091;&#1085;&#1082;&#1090;&#1099; &#1090;&#1072;&#1073;&#1083;&#1080;&#1094;&#1099; &#1088;&#1072;&#1079;&#1076;&#1077;&#1083;&#1086;&#1074; &#1088;&#1072;&#1089;&#1087;&#1086;&#1083;&#1086;&#1078;&#1077;&#1085;&#1099; &#1085;&#1077; &#1074; &#1076;&#1080;&#1089;&#1082;&#1086;&#1074;&#1086;&#1084; &#1087;&#1086;&#1088;&#1103;&#1076;&#1082;&#1077;

&#1044;&#1080;&#1089;&#1082; /dev/sdc: 100.0 &#1043;&#1041;, 100030242816 &#1073;&#1072;&#1081;&#1090;
255 heads, 63 sectors/track, 12161 cylinders
Units = &#1094;&#1080;&#1083;&#1080;&#1085;&#1076;&#1088;&#1099; of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d520cb8

&#1059;&#1089;&#1090;&#1088;-&#1074;&#1086; &#1047;&#1072;&#1075;&#1088;     &#1053;&#1072;&#1095;&#1072;&#1083;&#1086;       &#1050;&#1086;&#1085;&#1077;&#1094;       &#1041;&#1083;&#1086;&#1082;&#1080;   Id  &#1057;&#1080;&#1089;&#1090;&#1077;&#1084;&#1072;
/dev/sdc1   *           1       12161    97683201    f  W95 &#1088;&#1072;&#1089;&#1096;&#1080;&#1088;. (LBA)
/dev/sdc5               1          62      497920+  82  Linux &#1089;&#1074;&#1086;&#1087; / Solaris
/dev/sdc6            3840       12161    66846433+   7  HPFS/NTFS
/dev/sdc7              63        3839    30338721   83  Linux

&#1055;&#1091;&#1085;&#1082;&#1090;&#1099; &#1090;&#1072;&#1073;&#1083;&#1080;&#1094;&#1099; &#1088;&#1072;&#1079;&#1076;&#1077;&#1083;&#1086;&#1074; &#1088;&#1072;&#1089;&#1087;&#1086;&#1083;&#1086;&#1078;&#1077;&#1085;&#1099; &#1085;&#1077; &#1074; &#1076;&#1080;&#1089;&#1082;&#1086;&#1074;&#1086;&#1084; &#1087;&#1086;&#1088;&#1103;&#1076;&#1082;&#1077;

---

### Post by taurus on 2008-01-12
I assume you want to mount both /dev/sda5 & /dev/sdc6 permanently.

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```
/dev/sda5   /media/sda5   ntfs-3g   defaults   0   0
/dev/sdc6   /media/sdc6   ntfs-3g   defaults   0   0
```
Save it and close the gedit window.  Then, install ntfs-3g driver if you haven't done so and create those two new mount points.

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sda5 /media/sdc6
```
Now, reboot and those two partitions should be mounted to /media/sda5 and /media/sdc6, respectively.

```
df -h
```

---

### Post by descentspb on 2008-01-13
Thanks a lot, mate!

---

