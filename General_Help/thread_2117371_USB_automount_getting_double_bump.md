---
title: "USB automount getting double bump"
date: 2013-02-18
forum: General Help
---

### Post by yyyc186 on 2013-02-18
All,

I have been searching for and found a udev script which seems to automount USB sticks to /media.  The only problem, and I don't think it is a problem with this script directly, is each drive gets a "double bump".  Watching /media  shows sdb briefly, then it is replaced by sdb1 (when the stick has no label).

```
KERNEL!="sd*[!0-9]|sr*", GOTO="media_label_end"
KERNEL=="sd*[!0-9]|sr*", ATTR{removable}=="0" ENV{ID_SERIAL}!="?*", SUBSYSTEMS=="usb", IMPORT{program}="/sbin/blkid -o udev -p %N"
ENV{ID_FS_LABEL}!="", ENV{name}="%E{ID_FS_LABEL}"
ENV{ID_FS_LABEL}=="", ENV{name}="%k"

ACTION=="add", RUN+="/usr/bin/pmount --sync --noatime --umask 000 %k %E{name}"
ACTION=="remove", RUN+="/usr/bin/pumount %E{name}"

LABEL="media_label_end"

```


I "think" this script, which was for an earlier version of Debian is bumping into some existing udev rule.  I'm not good with udev scripts so would like someone to confirm/shoot down this thought.

The ghost causes a problem since the application looks to validate the mount and begin processing.  I would like to find a way to not get it.

Thanks

---

### Post by schragge on 2013-02-18
I'm not good with udev scripts either, but shouldn't there be a comma in there?
```

KERNEL=="sd*[!0-9]|sr*", ATTR{removable}=="0"[color=red],[/color] ENV{ID_SERIAL}!="?*", [color=blue]...[/color]

```

---

### Post by yyyc186 on 2013-02-19
Actually I'm 90% of the way there.

```
ACTION=="add",KERNEL=="sd[b-z][1-9]",ATTR{removable}=="1", SUBSYSTEMS=="usb", IMPORT{program}="/sbin/blkid -o udev -p %N"



KERNEL!="sd[b-z][1-9]", GOTO="media_label_end"
KERNEL=="sd[b-z][1-9]", ATTR{removable}=="1", SUBSYSTEMS=="usb", IMPORT{program}="/sbin/blkid -o udev -p %N"
ENV{name}="%k_%E{ID_FS_LABEL}"

ACTION=="add", RUN+="/usr/bin/pmount --sync --noatime --umask 000 %k %E{name}"
ACTION=="remove", RUN+="/usr/bin/pumount %E{name}"

LABEL="media_label_end"


```

The other thing you have to do is turn off automount in BOTH Nautilus and Dolphin via their respective tools and settings.

This rule works for all single partition thumb drives.  You do still see a temporary ghost when mounting a thumb drive with multiple partitions.  I suspect there is at least one more "default" or "standard" rule I need to kill off/override, but for now moving forward.

---

