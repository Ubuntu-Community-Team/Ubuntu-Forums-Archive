---
title: "[SOLVED] No swap after crash"
date: 2008-05-09
forum: General Help
---

### Post by ajgreeny on 2008-05-09
My system froze after a bad DVD+R I was using wouldn't write in k3b and I had to restart with the reset button.  Since then I have no swap enabled, and ```
sudo swapon /dev/hda5
```doesn't work, telling me /dev/hda5 is an invalid argument.  How can I get my swap back again?  Do I need to use gparted to reformat swap and then try swapon after I have edited fstab to get the UUID right?  (Or can I just use the /dev/hda5 as I used to in fstab?)

EDIT
Ok, it's all fixed by doing exactly what I asked about doing.  I did edit fstab after reformatting swap which was not recognised when I started gparted, so it had been corrupted by k3b.

---

