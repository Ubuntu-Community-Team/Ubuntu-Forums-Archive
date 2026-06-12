---
title: "Feisty: USB Devices Mount with Group root"
date: 2007-05-02
forum: General Help
---

### Post by disposable on 2007-05-02
After an upgrade from Edgy to Feisty, my USB devices that used to mount as user:user now mount as user:root. This breaks, for example, rsync with my Muvo2:

```
rsync: chgrp "/media/MUVO^2/podcasts/683.mp3" failed: Operation not permitted (1)
```

chgrp -R as root does not work. I've searched and found similar bugs, though no solution. It seems to be a HAL problem and that's where I'm currently researching.

Any help and ideas are appreciated.

---

### Post by disposable on 2007-05-02
Ok, this regression is a known problem and pmount is the workaround. Thanks to tehbizz at the binrev.com forums for the help.

---

