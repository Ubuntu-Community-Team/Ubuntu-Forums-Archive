---
title: "Name of mounted filesystem in nautilus"
date: 2007-04-25
forum: General Help
---

### Post by justinjstark on 2007-04-25
I managed to get my external drive to work nicely.  When I turn it on, it automatically mounts and nautilus pops open.  Hooray.  Here is my fstab entry:

```
/dev/sda        /mnt/External   ext3    noauto,user,rw,sync     0       0
```

When it's mounted, nautilus shows it as "/mnt/External" in the side-panel.  When it's not mounted, it shows it as "76.7 GB Volume."

Is there any way to get nautilus to just show "External" when mounted rather than "/mnt/External?"

---

### Post by justinjstark on 2007-04-25
Nevermind, it labels it "External" now.  I'm not sure whether it was due to the m2label that I gave the volume or not, but I'm happy.  :)

---

### Post by justinjstark on 2007-04-25
I just wanted to add something now that it is all sorted out.  This is awesome that ubuntu works with my external drive perfectly.  It automatically mounts when I turn it on.  When I unmount it, it is easy to remount it in nautilus.  When I turn the drive off, it disappears from nautilus side-bar entirely.  I have to say, this works better than I anticipated and it didn't take much to set up.  :guitar:

---

