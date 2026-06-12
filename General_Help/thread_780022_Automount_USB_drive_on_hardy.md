---
title: "Automount USB drive on hardy"
date: 2008-05-03
forum: General Help
---

### Post by 7marius on 2008-05-03
Hi,

Isn't there an option to disable automatic mounting of the partitions on my USB harddisk in hardy?

If possible I would like to mount only one of 3 partitions automatically, how is this done correctly?

Played around with fstab a bit, but it doesn't seem to have any effect.

Cheers
Marius

---

### Post by 7marius on 2008-05-04
Automount is handled by hald.
I disabled automount for the whole drive by creating a new file:

/etc/hal/fdi/policy/marius.fdi
```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="storage.serial" string="HTS42121_2H9AT00_DEF107679C83-0:0">
      <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      <merge key="volume.policy.should_mount" type="bool">false</merge>
    </match>
  </device>
</deviceinfo>

```

To find out your storage.serial, run lshal, and look for the corresponding drive (/dev/sdb).

I remember this was a simple GUI thing in warty, where is it hidden in hardy?
How can I tell hald to still mount one of the 3 partitions?

---

