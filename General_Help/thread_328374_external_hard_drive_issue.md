---
title: "external hard drive issue"
date: 2006-12-30
forum: General Help
---

### Post by typebox7000 on 2006-12-30
i have a maxtor one touch 80GB external hard drive.
maxtor has not made a linux compatible driver for this model.
is there a way to circumvent this issue, or a generic driver that i can use?

any help would be appreciated.

---

### Post by taurus on 2006-12-30
You don't need a driver for it!  Just plug it in and see if the automount will mount it or not.  If not, you can still mount it by hand and use it...

---

### Post by typebox7000 on 2006-12-30
it doesn't automount.
how do i mount it manually?

---

### Post by taurus on 2006-12-30
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by typebox7000 on 2006-12-30
Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2330    18715693+  83  Linux
/dev/hda2            2331        2434      835380    5  Extended
/dev/hda5            2331        2434      835348+  82  Linux swap / Solaris

---

### Post by taurus on 2006-12-30
Did you plug in your external harddrive to your machine (and turn on) because it didn't show up with that command?

---

### Post by typebox7000 on 2006-12-30
it is plugged in and turned on.
its not automounting.

---

### Post by taurus on 2006-12-30
What's the output of this command?

```
dmesg | tail
```

p.s.  It's a USB drive, right?

---

### Post by typebox7000 on 2006-12-30
[17179615.280000] apm: overridden by ACPI.
[17179621.156000] Bluetooth: Core ver 2.8
[17179621.156000] NET: Registered protocol family 31
[17179621.156000] Bluetooth: HCI device and connection manager initialized
[17179621.156000] Bluetooth: HCI socket layer initialized
[17179621.216000] Bluetooth: L2CAP ver 2.8
[17179621.216000] Bluetooth: L2CAP socket layer initialized
[17179621.296000] Bluetooth: RFCOMM socket layer initialized
[17179621.296000] Bluetooth: RFCOMM TTY layer initialized
[17179621.296000] Bluetooth: RFCOMM ver 1.7

---

### Post by typebox7000 on 2006-12-30
p.s.
it is USB.

---

### Post by typebox7000 on 2006-12-31
anyone?

---

