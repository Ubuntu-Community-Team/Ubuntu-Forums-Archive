---
title: "uswsusp installation problems"
date: 2008-06-08
forum: General Help
---

### Post by ChameleonDave on 2008-06-08
I've just installed the package "hibernate", and it brought in "uswsusp" (which apparently stands for "µswsusp") as a dependency.

When µswsusp installed, it came up with a cryptic error message:

```
Continue without a valid swap space?
```

There is a help button next to it, which brings up this message:

```

The swap file or partition that was found in uswsusp's configuration file is not active.  In most cases this means userspace software suspend will not work for you and you will need to choose (or let uswsusp choose) another swap space.  In some corner cases however, this can be what you want.

```

It gives no indication of what configuration file it is talking about, or how one might go about correcting the problem.

Here's the relevant part of my /etc/fstab file:

```

# /dev/sda1
UUID=21bbabd1-1b2d-43e0-8eb9-9513ed4c5edb none            swap    sw              0       0
# /dev/sdb1
UUID=b793bd32-eb43-4f92-9a70-0a7b52456e77 none            swap    sw              0       0

```

---

