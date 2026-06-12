---
title: "Window Title Bar Turns Green like Ooze"
date: 2008-06-01
forum: General Help
---

### Post by psilogon on 2008-06-01
More often than before, the title bar of windows turns green. I don't know if this is a side-effect of Linux or something to worry about. It scares me a little because I recently encountered a series of I/O buffer errors (errorno: -5) resulting from unplugging my USB Maxtor external hard drive from my computer. I am worried about the green title bar because I'm not sure whether it indicates underlying data corruption. Can anyone provide some comforting words? I was considering running *dpkg-reconfigure xserver-xorg* from recovery mode but decided it wasn't necessary. My xorg.conf and xorg.conf.bak files are perfectly intact and identical. As far as I can see, xorg.conf is not corrupted.

I've attached an image.

---

### Post by FuturePilot on 2008-06-01
That's a bug in Compiz. It has nothing to do with data corruption. But if you are getting errors from unplugging your USB hard drive you should make sure you unmount it first by right clicking on its icon and selecting "Unmount Volume"

---

### Post by psilogon on 2008-06-01
> **FuturePilot said:**
> That's a bug in Compiz. It has nothing to do with data corruption. But if you are getting errors from unplugging your USB hard drive you should make sure you unmount it first by right clicking on its icon and selecting "Unmount Volume"

Thanks. I will reinstall compiz components then. Do you think that will help or is this anomaly inherent and common? -- I unmounted the external hard disk before removing it but evidently didn't wait long enough after the icon disappeared from the desktop. I admit it was hasty! Thanks again, FuturePilot.

---

### Post by FuturePilot on 2008-06-02
You're welcome. :)
Reinstalling Compiz won't fix this. It's a bug in the software somewhere.

---

