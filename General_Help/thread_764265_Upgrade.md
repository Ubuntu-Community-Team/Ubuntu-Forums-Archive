---
title: "Upgrade?"
date: 2008-04-23
forum: General Help
---

### Post by dc-16 on 2008-04-23
Hi community,

I was just wondering, when Ubuntu 8.04 is released, I have it on free CD order. Will I be able to insert the CD and there be an upgrade option or will I have to completely reinstall Ubuntu?

Thanks,
DC

---

### Post by ibuclaw on 2008-04-24
Insert your DVD, Ubuntu should recognise that the DVD has a repository in it, and will ask if you want it added on.

Then you can do a:
```
sudo apt-get update && sudo apt-get upgrade
```

Although, the generally advertised option that the devs want you to use is:
```
sudo update-manager -d
```

After the DVD upgrade, reboot your computer.
When you come back, all your repositories should now be set to Hardy, so you can do a proper upgrade of your system.

Regards
Iain

---

