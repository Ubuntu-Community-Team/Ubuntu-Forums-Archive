---
title: "GPartEd problem"
date: 2008-06-07
forum: General Help
---

### Post by mastermatt63 on 2008-06-07
hey i have a Sony VAIO vgn fz140e that came pre installed with Vista Home Premium. whenever i pop in the gparted live cd and attempt to partition my internal hard drive that has vista on it, i can't do it. when i try and resize the drive the arrows won't move. There is a yellow caution sign next to the drive and i have no idea what it means. Thank you for your help in advance.

---

### Post by t.septekin on 2008-06-07
I have the Vaio FZ21M. You do realize that your hard drive may have two partitions, one for the Vaio Recovery (some 8-10 GB) and the other for the regular operation? You do not want to interfere with the recovery part! You can switch the drives listed in gparted by clicking on the arrows at top right.

You may try shrinking the Windows partition using Vista's own partition manager, then switch over to gparted live cd.

If your machine did not come with recovery discs, I would strongly recommend burning the discs before making any changes on your hard drive. Then have fun!

---

