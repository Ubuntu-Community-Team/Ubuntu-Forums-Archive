---
title: "On which Debian version is Ubuntu based?"
date: 2022-11-08
forum: General Help
---

### Post by fabi651 on 2022-11-08
Dear Community,

I have a general question to Ubuntu.

Ubuntu is based on Debian. But does anyone know on which Debian-Version Ubuntu 22.04 and 22.10 is based?

Thanks for your feedback!
Fabian

---

### Post by TheFu on 2022-11-08
It doesn't work exactly like that anymore - probably not in the last decade.

Different parts are taken from different versions of packages. Some from Debian Stable, some from Debian testing and some directly from the specific project teams. Canonical gets the source and recompiles it all for consistency in the toolchain and resulting programs.

This is part of the reason why grabbing any .deb file and forcing it to be installed under Ubuntu can break a system or will eventually break a system.
If you want a system that can be maintained more than 6 months, stick with Ubuntu Repos and trusted Ubuntu PPAs for the specific Ubuntu release.

---

### Post by MAFoElffen on 2022-11-08
Just as Fedora is the downstream testbed for RHEL, OpenSuse for SUSE, etc... Ubuntu 22.04's /etc/debian_release file says:
```

bookworm/sid

```
which says "SID", which is the Rolling DEV version of Debian, and "Bookworm" which is the next Stable Debian release planned for after "Bullseye".

Do not take that ***literal***, as TheFu explained, there are differences...

---

### Post by deadflowr on 2022-11-08
This (basically the same question) was asked and  answered on the Ubuntu Discourse site here: [https://discourse.ubuntu.com/t/which-debian-version-is-ubuntu-22-04-and-22-10-based-on/32036]("https://discourse.ubuntu.com/t/which-debian-version-is-ubuntu-22-04-and-22-10-based-on/32036")

---

### Post by fabi651 on 2022-11-10
Thanks a lot to you all, this was very informative to me :)

---

