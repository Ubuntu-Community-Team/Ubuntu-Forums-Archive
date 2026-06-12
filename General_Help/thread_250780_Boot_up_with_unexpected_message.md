---
title: "Boot up with unexpected message"
date: 2006-09-04
forum: General Help
---

### Post by JamesB on 2006-09-04
I am running a dual boot system with fat32 and raiserfs partitions. When I boot up, as the file systems are being checked, the screen goes into text mode. There seems to be no adverse effects. It seems to happen when checking the fat32 partitions. Does anyone know why this would happen? It's rather ugly and doesn't look good.

---

### Post by orb9220 on 2006-09-04
boot up splash will abort to text if a hd fs is being checked.

You can disable the check by changing the 2 to 0 at the end of the fstab entry for the drive. This will disable checking for the drive.

---

### Post by JamesB on 2006-09-05
Thank you, now boots up in record time!! hurray

---

