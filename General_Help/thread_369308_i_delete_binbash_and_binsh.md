---
title: "i delete /bin/bash and /bin/sh"
date: 2007-02-24
forum: General Help
---

### Post by mitjab on 2007-02-24
By mistake i delete /bin/bash and /bin/sh. Now i can not use ubuntu any more?

What can i do?

---

### Post by tgalati4 on 2007-02-24
boot the live cd into rescue mode and copy them back.

mount /dev/hda1     (your drive may be hda1, hda2, hdb1, hdb2 etc)
cp /bin/bash /mnt/hda1/bin
cp /bin/sh /mnt/hda1/bin

shutdown -h now

remove disk and reboot.

---

