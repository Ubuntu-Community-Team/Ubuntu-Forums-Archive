---
title: "ColdFusion 6.1"
date: 2005-09-13
forum: General Help
---

### Post by leaded on 2005-09-13
Has anyone successfully installed CFMX 6.1 on Ubuntu? I've read of success with 7.0, but we have a 6.x license. I'm having a heck of a time getting it to work on Fedora 4 64-bit so I was thinking about trying Ubuntu. I ran the installer and it missed some dependencies (which in FC4 was compat-libstdc++, which I didn't see for Ubuntu). Anyone help? I can provide more info on my system... thanks!

---

### Post by sdhoigt on 2006-07-19
> **leaded said:**
> Has anyone successfully installed CFMX 6.1 on Ubuntu? I've read of success with 7.0, but we have a 6.x license. I'm having a heck of a time getting it to work on Fedora 4 64-bit so I was thinking about trying Ubuntu. I ran the installer and it missed some dependencies (which in FC4 was compat-libstdc++, which I didn't see for Ubuntu). Anyone help? I can provide more info on my system... thanks!

Check this how-to for installing CFMX 7 on Debian.  It discusses the issue you're seeing.

[http://www.howtoforge.com/coldfusion_installation_debian_sarge](http://www.howtoforge.com/coldfusion_installation_debian_sarge)

I haven't finished the how-to yet, but for starters you'll need to make sure the following packages are installed.
libstdc++6 libstdc++5 libstdc++2.10-glibc2.2

SD

---

