---
title: "Where is the Restricted Drivers Manager?"
date: 2008-05-09
forum: General Help
---

### Post by neptuneg on 2008-05-09
I don't have the restricted drivers manager or any kind of device manager.  I tried to find it with add/remove but couldn't.  Any ideas?

---

### Post by ugm6hr on 2008-05-09
System->Adminstration->Hardware Drivers

It's had a name change in the menu, but is basically the same thing.

---

### Post by neptuneg on 2008-05-09
Thanks.  Nothing is listed though.  Any idea why that could be?

---

### Post by ugm6hr on 2008-05-09
> **neptuneg said:**
> Thanks.  Nothing is listed though.  Any idea why that could be?

1. You don't have any proprietary drivers / hardware.
2. You are not online.

Maybe you are asking the wrong question.  What are you trying to do?

---

### Post by neptuneg on 2008-05-09
I am not online with that machine.

My network card is not working correctly at all.  I've followed a bunch of guides to using ndiswrapper, but I don't have any luck. It seems that wlan0 is taking on the wrong driver (b43xx or something).  I want to have it use ndiswrapper.

---

### Post by ugm6hr on 2008-05-10
This sounds like a wifi problem.

Do you have wired ethernet connection?  Is the wifi card internal or USB?

I suspect you have a Broadcom chipset.

If you want to get it to work, I would suggest you start a new thread with this information, together with the output of these commands:

```
lspci
lsusb
lshw -C network
```

---

