---
title: "New Swap Partition Not Working"
date: 2015-10-13
forum: General Help
---

### Post by cobalt2 on 2015-10-13
I had to delete the swap space in order to resize my lvm partition. Since recreating the swap space and editing fstab to replace the old UUID with the new one, the swap isn't working properly. Suspend and hibernate doesn't work. I changed the name of the swap space from swap_1 to swap. Could this be the cause of this problem?

---

### Post by sammiev on 2015-10-13
[This]("http://askubuntu.com/questions/33697/how-do-i-add-a-swap-partition-after-system-installation") has help me in the past.

---

### Post by cobalt2 on 2015-10-14
Now I see where I went wrong. I forgot to change the name of the swap space in fstab. Problem solved.

---

