---
title: "Firefox Updates"
date: 2007-01-28
forum: General Help
---

### Post by acmethunder on 2007-01-28
I ran update manager this morning, and it does not seem to recognize that I no longer have Firefox 1.5 (I now use Firefox 2.0).  I deselected the Fx 1.5 updates, yet when checked ater on, the update manager said I still had 3 updates left, so I have ignored them for now.

Do I need these updates...I am assuming not because it is for an older version of Firefox.  If not, will keep receiving the update notifications for Firefox 1.5?

---

### Post by tito2502 on 2007-01-28
If you manually upgraded to firefox 2 then you should uninstall the 1.5 version packaged with dapper.

---

### Post by aysiu on 2007-01-28
> **tito2502 said:**
> If you manually upgraded to firefox 2 then you should uninstall the 1.5 version packaged with dapper.
Actually, no, you shouldn't, according to this page:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

You can, however, lock the package version for 1.5 using Synaptic.

---

### Post by eeried on 2007-03-05
How long will Dapper be able not to run Firefox2 -- Firefox 1.5 won't be supported for much longer by the Mozilla team.  I've read here the Ubuntu team would support firefox 1.5 for another two years but that means incredible work with the code while packaging is rather less painful. Maybe I'm very ignorant of what the maintainers do.

Installing Firefox 2 is no problem for some of us but it is for the general public -- especially the update process is tricky (chmod or root). I've read here that Firefox2.deb would make Dapper unstable --  Firefox2.tgz on Dapper runs fine and doesn't seem to make things unstable.

Cheers,

---

### Post by yabbadabbadont on 2007-03-05
> **eeried said:**
> How long will Dapper be able not to run Firefox2 -- Firefox 1.5 won't be supported for much longer by the Mozilla team.  I've read here the Ubuntu team would support firefox 1.5 for another two years but that means incredible work with the code while packaging is rather less painful. Maybe I'm very ignorant of what the maintainers do.

Installing Firefox 2 is no problem for some of us but it is for the general public -- especially the update process is tricky (chmod or root). I've read here that Firefox2.deb would make Dapper unstable --  Firefox2.tgz on Dapper runs fine and doesn't seem to make things unstable.

Cheers,

Actually, Debian would most likely be the one to maintain it.  Then Ubuntu would repackage the Debian version.  Which, I believe, is pretty much what happens now.

---

