---
title: "dpkg not working on any distro i use"
date: 2006-11-28
forum: General Help
---

### Post by HokeyFry on 2006-11-28
in the past few days i have installed several distros of ubuntu on my laptop. I started with breezy, upgraded to dapper, reinstalled to edgy, then reinstalled to breezy again. the reason i did all this was because dpkg does not work on any distro i use. for example, if i try to install vlc thru dpkg this is what happens:

```

alexander@d47-69-99-55:/media/REDFLASH/vlcpackages$ sudo dpkg -i vlc_0.8.4-svn2$
Password:
dpkg-deb: unexpected end of file in version number in vlc_0.8.4-svn20050920-3+h$
dpkg: error processing vlc_0.8.4-svn20050920-3+hal0ubuntu3_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 vlc_0.8.4-svn20050920-3+hal0ubuntu3_i386.deb

```

i have no idea what this error means or how to fix it

thanks in advance for any help

---

