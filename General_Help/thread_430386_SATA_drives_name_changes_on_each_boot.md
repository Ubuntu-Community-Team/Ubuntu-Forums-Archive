---
title: "SATA drives name changes on each boot"
date: 2007-05-02
forum: General Help
---

### Post by cstrom on 2007-05-02
Hi Ubuntuers,

I had a very annoying problem that I'm not entirely sure how to solve. Each time I boot my computer my SATA drives will have new names, ie. sometimes SDA will become SDE. Now I think this can be solved with UDEV, but I'm not that experienced with creating custom rules in UDEV, assuming that's the source of the problem.

Perhaps it's the "start-up" program in Ubuntu that discovers drives and devices in a parallell fashion.

Any help is appreciated.

Regards,
Chris

---

### Post by gerscht on 2007-05-02
can you post the contents of your /etc/fstab please?

you want to replace the /dev/sde1 against the UUID of the drive.
To find out the drives UUID use
```
tune2fs -l /dev/sde1
```

Gerscht

---

### Post by cstrom on 2007-05-02
Thank you. I've replaced all /dev/ names in my fstab with the UUID of the particular partition and that works great.

Thanks for your help!

/ Chris

---

