---
title: "&quot;Writing data to device&quot; Why so late?"
date: 2008-02-24
forum: General Help
---

### Post by schmolch on 2008-02-24
Hey there!

When i write like 1GB on my SD Card and leave the Laptop alone for 1h this should be more than enough time to complete the write-process, right?
But when i return after 1h and select Unmount it starts writing data to the device for a couple of minutes and i have to wait.

Why isn't it doing this as soon as possible and waits until i want to remove it???????????

I smell a bugreport here :-)

---

### Post by dcstar on 2008-02-24
> **schmolch said:**
> Hey there!

When i write like 1GB on my SD Card and leave the Laptop alone for 1h this should be more than enough time to complete the write-process, right?
But when i return after 1h and select Unmount it starts writing data to the device for a couple of minutes and i have to wait.

Why isn't it doing this as soon as possible and waits until i want to remove it???????????

I smell a bugreport here :-)

One hour is far too long, Linux will cache writes for removable devices but not for that long - is there something left running doing reads to the device?

---

### Post by schmolch on 2008-02-24
I tried again and this time the unmounting was without delay.
I'll keep observing this.

---

