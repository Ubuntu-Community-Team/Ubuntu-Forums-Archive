---
title: "help with vmware"
date: 2007-06-18
forum: General Help
---

### Post by Irti on 2007-06-18
i installed vmware a few days back.....then i realised for some reason that i didnt want it anymore so i uninstalled it.......but the space that i set aside for mounting xp on vmware is still not freed up as my total available memory should br 32 gb ...instead i get only 17 gb.....how do i get that space back...????????????

---

### Post by H.E. Pennypacker on 2007-06-18
You can always delete the hidden folder that remains even after you have uninstalled VMware.  Go to your home folder, press CTRL-H (or select View > Show Hidden Folders), and locate .vmware (notice the period before the folder name - your folder name may actually be different).  Delete the entire folder.

Edit:  Use Disk Usage Analyzer (Applications > Accessories) to determine what is taking up space.

---

### Post by Irti on 2007-06-18
ok i solved it.....it was like in my /var/lib/vmware-server/       there was an xp folder that was what i installed into vmware.........i just had to delete that.....

---

