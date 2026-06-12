---
title: "External HDD and the ghosts that are haunting it."
date: 2007-12-19
forum: General Help
---

### Post by kevCast on 2007-12-19
I recently purchased a MyBook essential 320 GB external HDD. I repartitioned it, and put Slackware on it. Slackware kernel panicked and wouldn't boot. I pulled up cfdisk and deleted every partition on it and reformatted with a W95 Fat 32 (the type of partition that was on it before I tinkered). Even though it says I overwrote it on cfdisk, every time I open the drive in Ubuntu it shows me the Unix system file hierarchy from Slackware.

How would I go about completely wiping this thing of everything and start new?

---

### Post by solar george on 2007-12-19
Did you remember to do,

```
mkdosfs /dev/*device*
```

---

### Post by kevCast on 2007-12-19
Why would I do that?

*Edit: Nevermind, got it working. Thank you solar george.*

---

