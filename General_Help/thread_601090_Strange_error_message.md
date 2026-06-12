---
title: "Strange error message"
date: 2007-11-02
forum: General Help
---

### Post by ThinkDave on 2007-11-02
Im getting a strange error message im my dmesg output anyone know whats going on?
```
Nov  3 12:35:29 unilinux-desktop kernel: [ 1752.719854] sd 0:0:0:0: [sda] Unit Not Ready
Nov  3 12:35:29 unilinux-desktop kernel: [ 1752.719861] sd 0:0:0:0: [sda] Sense Key : No Sense [current] 
Nov  3 12:35:29 unilinux-desktop kernel: [ 1752.719865] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
Nov  3 12:35:30 unilinux-desktop kernel: [ 1753.516061] sd 0:0:0:0: [sda] READ CAPACITY failed
Nov  3 12:35:30 unilinux-desktop kernel: [ 1753.516068] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov  3 12:35:30 unilinux-desktop kernel: [ 1753.516073] sd 0:0:0:0: [sda] Sense Key : No Sense [current] 
Nov  3 12:35:30 unilinux-desktop kernel: [ 1753.516076] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
Nov  3 12:35:30 unilinux-desktop kernel: [ 1753.781794] sd 0:0:0:0: [sda] Test WP failed, assume Write Enabled
Nov  3 12:35:31 unilinux-desktop kernel: [ 1754.029544] sd 0:0:0:0: ioctl_internal_command return code = 8000002
Nov  3 12:35:31 unilinux-desktop kernel: [ 1754.029550]    : Sense Key : No Sense [current] 
Nov  3 12:35:31 unilinux-desktop kernel: [ 1754.029554]    : Add. Sense: No additional sense information
```

---

### Post by rsambuca on 2007-11-02
That doesn't make any sense to me.

---

### Post by ThinkDave on 2007-11-02
> **rsambuca said:**
> That doesn't make any sense to me.

You and me both. I think it might have something to do with it trying to find my USB thumb drive which isn't installed. Or if its trying to find a sata device that might be it cause i have no sata hard drives. Im just guessing i really would like to stop it though so it leaves my dmesg output free.

---

