---
title: "Clutter Buildup?"
date: 2007-09-19
forum: General Help
---

### Post by Flashstar on 2007-09-19
I am a fairly strict Windows user just because I need to be. For example, none of my games work on Linux (I don't like losing speed in Wine/ Cedega). Anyway, I'm just wondering if over time clutter builds up on Linux as much as Windows. I'm interested because I always do a reinstall on Windows every 5-6 months due to clutter (old files/ junk) building up.

Thanks

---

### Post by apetresc on 2007-09-19
> **Flashstar said:**
> I am a fairly strict Windows user just because I need to be. For example, none of my games work on Linux (I don't like losing speed in Wine/ Cedega). Anyway, I'm just wondering if over time clutter builds up on Linux as much as Windows. I'm interested because I always do a reinstall on Windows every 5-6 months due to clutter (old files/ junk) building up.

Thanks
As a general rule, no. This is partially due to better design decisions on UNIX systems' parts, like the lack of a registry, and in part due to Ubuntu's central software repository that makes sure all the software on your system installs and uninstalls itself in a unified way.

If you want to be sure extra controlling of things like conf files, always remove files with ```
sudo apt-get remove --purge packagename
``` instead of just ```
sudo apt-get remove packagename
``` The --purge will delete configuration files as well as just system files.

---

