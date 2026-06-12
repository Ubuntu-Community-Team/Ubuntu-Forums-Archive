---
title: "Change f-spot photo directory"
date: 2006-10-26
forum: General Help
---

### Post by hanzomon4 on 2006-10-26
How do you change the default photo directory in f-spot?

---

### Post by tom56 on 2006-11-13
Very late reply, I know, but I'm searching for a solution to the same problem. It can't be done - see my bug: [https://launchpad.net/distros/ubuntu/+source/f-spot/+bug/69567](https://launchpad.net/distros/ubuntu/+source/f-spot/+bug/69567)

---

### Post by hanzomon4 on 2006-11-28
Thanks for the link, Any idea when/if this will be fixed

---

### Post by hanzomon4 on 2006-11-28
I built v0.2.2 from src and it allowed me to change the photo dir.

---

### Post by irw on 2007-02-12
Apparently this is already available in the options in Edgy.

The other alternative is to create a link to your photo directory named "Photos" in your home directory.  This then means that f-spot will load your photos into Photos, but in reality this will be where-ever you have pointed it at.

Eg: ```
sudo ln -s /where-you-want-your-photos ~/Photos
```

---

