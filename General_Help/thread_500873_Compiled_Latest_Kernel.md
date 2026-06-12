---
title: "Compiled Latest Kernel"
date: 2007-07-14
forum: General Help
---

### Post by skymera on 2007-07-14
as said, last night i compiled the latest Linux Kernel.
works great!

BUT, in Network, i ONLY have Wired or Dial Up.
there is no wireless, which i have

is tghere a way i can add it to the Kernel?

or is it more complicated?

---

### Post by geraldm on 2007-07-14
wireless is in the kernel in the form of drivers for wireless devices.  Look in
/lib/modules/`uname -r`/kernel/drivers/net/wireless

To use wireless, you also have to have a package such as wireless-tools.

Gerald

---

