---
title: "issue mounting sd card"
date: 2016-10-10
forum: General Help
---

### Post by alain.roger on 2016-10-10
Hi,

i was thinking to automatically mount the sdcard using fstab.
My sd card reader works well for reading mode, but i'm not able to write on the sdcard.

therefore i tried several things to make the sdcard in r/w mode but without success.

e.g.:
```
sudo mount --options remount,rw /dev/mmcblk0p1 /media/alain/sdcard

```

but i get the following error message:
```
mount: /media/alain/sdcard not mounted or bad option

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

checking the syslog, i got:
```
[  862.894015] mmcblk0: r/w command failed, status = 0x80000900
[  863.400883] mmc0: tried to reset card
[ 1003.998207] mmcblk0: r/w command failed, status = 0x80000900
[ 1004.372440] mmc0: tried to reset card

```

i would like to understand:
1. what is for ubuntu "reset card" ? is it "formating" the sdcard ?
2. how to mount / remount sdcard in read/write mode as standard commend for sdcard in exfat is not working also (sudo mount -f exfat /dev/mmcblk0p1 /media/alain/sdcard/)

thx.

---

### Post by sudodus on 2016-10-10
Did you create the mountpoint?

```
sudo mkdir /media/alain/sdcard
```

Some people prefer to create manual and custom mountpoints in the /mnt directory, so

```
sudo mkdir /mnt/sdcard
```

and

```
sudo mount /dev/mmcblk0p1 /mnt/sdcard
```

should work (without any options), but if you want all users to have full access to the partition on the card, you can use the following command line

```
sudo mount -o rw,users,umask=000 /dev/mmcblk0p1 /mnt/sdcard
```

---

### Post by alain.roger on 2016-10-10
Mounted point is created.

if i use:
```
[FONT=monospace][COLOR=#000000]sudo mount /dev/mmcblk0p1 /media/alain/sdcard  [/COLOR]
[/FONT]
```

i get:
```
[FONT=monospace][COLOR=#000000]FUSE exfat 1.2.3[/COLOR]
WARN: '/dev/mmcblk0p1' is write-protected, mounting read-only.
WARN: volume was not unmounted cleanly.
[/FONT]
```

same result if i specify "[COLOR=#000000][FONT=Ubuntu Mono]-o rw,users,umask=000" so for all users.[/FONT][/COLOR]

even if i unmount sdcard with:
```
sudo umount /media/alain/sdcard
```

so i'm confused...  sdcard is always in read only mode :(

---

### Post by sudodus on 2016-10-10
**exfat** is a proprietary Microsoft file system, which has limited support in linux. But you can install two exfat packages

```
sudo apt-get install exfat-utils exfat-fuse
```

and try again.

See this link to ***Ask Ubuntu*** for more details: [How to get a drive formatted with exfat working?](https://askubuntu.com/questions/370398/how-to-get-a-drive-formatted-with-exfat-working)

---

