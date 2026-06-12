---
title: "Filesystem read only error?"
date: 2007-05-05
forum: General Help
---

### Post by cd-r80 on 2007-05-05
/root mounts only read only (dev/hda7) So I got: "Filesystem read only error?" when using nano /etc/apt/sources.list & I try to save.

/var/log/messages:May  5 15:45:32 localhost kernel: [4295853.323000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }

but:

e2fsck 1.38 (30-Jun-2005)
/dev/hda7: recovering journal
/dev/hda7: clean, 42979/1602496 files, 286590/3200943 blocks

smartctl: no problems in my hd...

Can I remove "(rw,errors=remount-ro)"  that errors=remount -ro part? Or is it dangerous?

---

### Post by taurus on 2007-05-05
```
**sudo** nano /etc/apt/sources.list
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by cd-r80 on 2007-05-05
Not that because I had: sudo su...

---

### Post by taurus on 2007-05-05
You did reboot, right?

---

