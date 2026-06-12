---
title: "Why do I need 3 Kernels?"
date: 2018-01-13
forum: General Help
---

### Post by emarkay on 2018-01-13
I have 16.04 and it updates Linux 04.04 and 04.10 and 04.13.  Can I delete the others? - I presume 04.13 is the newest?

Thanks!
MRK

---

### Post by deadflowr on 2018-01-13
You probably have the hwe packages installed and the regular linux-generic (or linux-image-generic and linux-headers-generic) packages installed.
You want the hwe packages as those are what install the 4.13 kernels.
But you do not need the regular generic packages as those are what install the 4.4 kernels.

The 4.10 kernels are done with now, and you will not get any more of those.

So in short yes you can remove the kernels you do not want anymore, such as the 4.4 kernels.
I would suggest simply removing the linux-generic package or if that is not actually installed the linux-image-generic and linux-headers-generic packages.
That will prevent that particular kernel (the 4.4 kernels) from updating any more, then you can just remove any existing 4.4 kernels.

I would not be surprised if the 4.4 kernels are listed for removal when you run
```
sudo apt autoremove --purge
```

(I wouldn't sweat the 4.10 kernel since it was the last version as they have moved up the hwe stack to 4.13.
But since the design is to keep the last kernel it's best to keep it until another 4.13 kernel gets installed, then you can remove it.)


Reference of HWE:[https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

Any of that make sense?
Or was that just incoherent

---

### Post by emarkay on 2018-01-13
Awesome - 4.10 is gone. But when I try to remove 4.4, it wants to remove "linux-gerenric" and "linux-extra-generic".  OK to remove these?  Is there a performance benefit in removing these?  THANKS!
MRK

---

### Post by deadflowr on 2018-01-13
> **emarkay said:**
> Awesome - 4.10 is gone. But when I try to remove 4.4, it wants to remove "linux-gerenric" and "linux-extra-generic".  OK to remove these?  Is there a performance benefit in removing these?  THANKS!
MRK

Yep those are fine to remove.
They are ineffective if using the 4.13 kernels, so performance issues are moot. more likely space saving.
And removing those will stop the 4.4 kernels from getting new updates.
Benefits all around to removing them.

What you do want are the hwe-16.04 packages, anything else is just a waste of hard drive space, imo.
(the hwe packages will keep the 4.13 kernels updated)

Hope that make sense.

---

