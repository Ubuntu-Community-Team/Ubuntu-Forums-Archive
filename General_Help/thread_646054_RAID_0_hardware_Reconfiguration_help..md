---
title: "RAID 0 hardware Reconfiguration help."
date: 2007-12-20
forum: General Help
---

### Post by Ocxic on 2007-12-20
I currently have a RAID 0 array with a 120GB IDE drive and 250GB SATA drive as follows:

/boot partiton on 120GB IDE
/ (root) partiton RAID partition 1 IDE and SATA
/Storage RIAD partition 2 IDE and SATA
SWAP RAID partition 3 IDE and SATA

I am getting a new 250GB SATA drive and wish to replace my current 120GB IDE drive. I currently have 225GB of data in my storage partition and no way to backup currently (without useing 50 DVDs). Is there a way to make this change without harming/losing the data on my /Storage partition. I do not care if I have to re-install.

thanks

---

### Post by Ocxic on 2007-12-24
bump

---

### Post by burbankmarc on 2007-12-24
use dd. I'd suggest booting into a live disc or something

then do this:

```
dd if=/dev/sda1 of=/dev/sda2 bs=2048
```

where sda1 is your old HDD, and sda2 is your new HDD. dd is a low level copy util.

---

