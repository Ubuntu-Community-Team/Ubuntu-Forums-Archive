---
title: "Boot issue"
date: 2008-02-13
forum: General Help
---

### Post by Chrisv006 on 2008-02-13
Will having more than 4 partitions (with ubuntu on the fifth) keep ubuntu from booting?  it just hangs. no errors.   in grub when i press 'e' and get to kernel (where it gives the uuid and the splash) and press 'tab' to test the string, it gives an error.  I checked and the uuid in the menu.lst is the correct root partition.  any one know if going down to just 3 partitions will let it boot?  (sorry about the formattins. typed this on my phone from work. )

---

### Post by Existentialist on 2008-02-13
It shouldn't cause any problems.  How are your partitions set up?  Is Ubuntu on one of the primary partitions or one of the logical?  And at which part of booting exactly is it hanging?

---

### Post by Chrisv006 on 2008-02-13
I just got it.


I had two monitors hooked up...when I unplugged the VGA port one it booted perfectly.

Now - when I put the Nvidia drivers on, can I run dual screens?

Thanks,
Chris

---

### Post by Existentialist on 2008-02-13
Once you have the Nvidia drivers installed you should be able to go in to the nvidia-settings and set up the dual monitors.

---

