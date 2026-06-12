---
title: "Chromebook Unity &quot;Sub-process /usr/bin/dpkg returned an error code (1)&quot;"
date: 2013-08-14
forum: General Help
---

### Post by tim_tang2 on 2013-08-14
So I've already looked at several different questions regarding the issue of "Sub-process /usr/bin/dpkg returned an error code (1)", but none of the fixes worked for me. I'm running Unity on my Chromebook and received this error when trying to install Sublime Text 3 via PPA.

The error begins here:
"sublime-text-installer failed to preconfigure, with exit status 20
...
dpkg: error processing /var/cache/apt/archives/sublime-text-installer-3047-2~webupd8~3_all.deb (--unpack):
subprocess new pre-installation script returned error exit status 128
Errors were encountered while processing: /var/cache/apt/archives/sublime-text-installer-3047-2~webupd8~3_all.deb
E: Sub-process /usr/bin/dpkg returned and error code (1)"

Thanks in advance to anyone who can help me figure out what's going on!

---

### Post by ian-weisser on 2013-08-14
Tell the PPA maintainer. They need to know that their install script is broken.

---

