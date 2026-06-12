---
title: "Where is my sda mounted?"
date: 2007-05-22
forum: General Help
---

### Post by GabrielWolff on 2007-05-22
Hey,

I got some problems and am trying to recover my data.

OPne of the problems is with the xorg (I guess). I get no logon screen, so I'm trying to get along in "white text on black screen mode".

Actually that ain't that bad, I just can't find out where my sda is mounted. I forgot, and don't seem to be able to find it. There is no sda under /dev.

Where is it mounted.

How do I copy files to it?

Gabriel

---

### Post by Martje_001 on 2007-05-22
Under /dev you only find device-files. You have to search in /media.

---

### Post by taurus on 2007-05-22
Are you currently booting from the LiveCD or from your harddrive?

```
sudo fdisk -l
```

---

### Post by GabrielWolff on 2007-05-22
Mounting from the hard drive.

sudo fdisk -l gives me:
all kinds of bla bla and then:
Disdk /dev/sda: 2045 Mb ....... bla bla
and later then:
/dev/sda1 .... bla

under /media I find: cdrom cdrom0 floppy floppy0 My Book USB usbstick

But none of them is the mounted volume, I think. On the device that was mounted at /dev/sda there are several  files, and the only device I can enter is USB, and there's nothing.

Sorry for the partial info, I'm kinda confused...
G

---

### Post by taurus on 2007-05-22
It would be nice if you could post the whole and complete output here instead of the bla bla bla.  Bla bla bla is not really helping at all.

```
sudo fdisk -l
df -h
```

---

### Post by GabrielWolff on 2007-05-22
```
gabriel@gabriel:"$ sudo fdisk -l
Password:

Disk /dev/hda: 40.0 GB, 40007761920 bytes

Device Boot      Start     End     Blocks     Id     System
/dev/hda1         1          4864     39070048+  5  Extended
/dev/hda5*       1          31       248944+       83   Linux
/dev/hda6         1          32        38821041     8e   Linux LVM

Disk /dev/sda: 2045 MB, 2045771776 byte  s
63 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes

Device Boot      Start     End     Blocks     Id     System
/dev/sda1        1             1023  1997700+  6   FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
  phys=(0, 3, 59) logical (0, 3, 62)
Partition 1 has different physical/logical endings:
  phys=(990, 62, 62) logical (1022, 59, 58)
gabriel@gabriel:"$
```

```
Gabriel@gabriel~$ df -h
Filesystem         size     Used    Avail    Use%   Mounted on
/dev/mapper/Ubuntu/root
                         36G     31G      2.9G     92%   /
varrun              221M    76K      221M   1%     /var/run
varlock              221M    4.0K    221M   1%     /var/lock
udev                 221M    96K      221M   1%     /dev
devshm            221M        0       221M   0%     /dev/shm
lrm                    221M    19M      202M   9%     /lib/modules/2.6.15-28-386/volatile
/dev/hda5        228M     31M     185M   15%   /boot
gabriel@gabriel:~$
```

---

### Post by taurus on 2007-05-22
Do you need to edit /etc/X11/xorg.conf to fix your X?

```
sudo nano -Bw /etc/X11/xorg.conf
```
<Ctrl>o to save and <Ctrl>x to exit.

---

### Post by GabrielWolff on 2007-05-22
I'm not entirely sure what you mean.
How shoudl I edit it?
What should I change?

G

---

