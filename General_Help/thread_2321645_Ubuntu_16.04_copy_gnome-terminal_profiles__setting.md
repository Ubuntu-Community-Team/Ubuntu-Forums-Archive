---
title: "Ubuntu 16.04 copy gnome-terminal profiles / settings to multiple machines"
date: 2016-04-23
forum: General Help
---

### Post by worthspending on 2016-04-23
Just installed Ubuntu 16.04.  I have several machines.  I would like to configure the profiles / settings for gnome-terminal on one machine and copy those profiles / settings to all of my other machines.

How can I copy the profiles / settings to multiple machines?

Thanks

---

### Post by aglick on 2016-05-03
I had this same question and after grepping through my entire drive for a unique profile name I found that all the profiles are stored in dconf (replacement to gconf)

```
dconf list /org/gnome/terminal/legacy/profiles:/
```

---

