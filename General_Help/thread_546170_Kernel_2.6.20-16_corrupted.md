---
title: "Kernel 2.6.20-16 corrupted"
date: 2007-09-08
forum: General Help
---

### Post by Mal1024 on 2007-09-08
I recently used the Update Manager to install a Linux kernel update. However, I believe the computer was shut down (by another family member) before the update completed. Whenever I boot, I have to boot kernel 2.6.20-15, or the system just hangs on the splash screen. Is there a way that I can fix this problem, or would it be easier to wipe the Linux partition and reinstall?

---

### Post by sumguy231 on 2007-09-08
Have you tried 
> sudo aptitude reinstall linux-image-2.6.20-16-generic?

---

### Post by Mal1024 on 2007-09-09
Thanks, that fixed it.

---

