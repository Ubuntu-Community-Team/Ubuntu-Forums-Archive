---
title: "Ubuntu / XP dual boot"
date: 2007-03-20
forum: General Help
---

### Post by grimgrim on 2007-03-20
Hello all,

I've been running ubuntu since about the release of breezy and I'm very happy with it. Just yesterday I decided I couldn't easily do without a certain Windows app, and so I took a deep breath, and prepared to install Win XP.

My setup is such that I have a 160Gb drive as my primary master, which is totally given to ubuntu. I also have a 30Gb drive as primary slave, which I had been using for backup storage, but now want to use for XP.

To install XP on primary slave, I unplugged primary master from the IDE cable and ran a normal install. All went smoothly and I have a working XP installed on primary slave.

I plugged primary master back in and added the following to menu.lst:

```
grim@goat:~ $ cat /boot/grub/menu.lst
(...)
title           Windows XP
root            (hd1,0)
savedefault
makeactive
chainloader     +1
```

But it seems I was too optimistic as XP does not boot when this option is selected.

So the question I must ask of you folks is this: have I gone completely the wrong way about it? What can I do about it?

Any help would be appreciated.

---

### Post by Kateikyoushi on 2007-03-20
I would try to change root to (hd2,0).
If still won't work then show us the output of this.

> sudo fdisk -l

---

### Post by brynk on 2007-03-20
Also, if it's just one application you can't do without you might want to consider using emulation software like wine or vmware.

---

### Post by grimgrim on 2007-03-20
> **Kateikyoushi said:**
> I would try to change root to (hd2,0).
If still won't work then show us the output of this.

Ok, I'll try that, but I'm doubtful, and here's why:

```
 grim@goat:~ $ cat /boot/grub/device.map
(hd0)   /dev/hda
(hd1)   /dev/hdb
```

In the meantime, here's the partitioning report from fdisk:

```
grim@goat:~ $ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19395   155790306   83  Linux
/dev/hda2           19396       19457      498015    f  W95 Ext'd (LBA)
/dev/hda5           19396       19457      497983+  82  Linux swap / Solaris

Disk /dev/hdb: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3735    30001356    7  HPFS/NTFS
```

---

### Post by grimgrim on 2007-03-20
Here's what I see when selecting XP to boot from:

```
root (hd1,0)
Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1
_
```

Where the underscore on the last line represents a blinking cursor.

Cursory googling on the "filesystem unknown" error suggests I might get further if I specify "rootnoverify" rather than root, so I'll try that next.

---

### Post by grimgrim on 2007-03-20
Still no luck. Setting rootnoverify bypasses the "Filesystem type unknown" error (duh) but doesn't let booting progress any further than before.

Here's an interesting link which will be my next line of attack:
[http://paul.boin.org/archives/26-Grub-and-NTFS-Unknown-partition-type-0x7.html](http://paul.boin.org/archives/26-Grub-and-NTFS-Unknown-partition-type-0x7.html)

---

### Post by Kateikyoushi on 2007-03-20
Yes you were right, hd1,0 should have worked.

---

