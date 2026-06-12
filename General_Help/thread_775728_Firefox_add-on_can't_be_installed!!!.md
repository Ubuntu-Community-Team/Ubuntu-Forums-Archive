---
title: "Firefox add-on can't be installed!!!"
date: 2008-04-30
forum: General Help
---

### Post by kakyoism on 2008-04-30
[Machine]
Sony VAIO VGN-NR298D

[System]
ubuntu 8.04

[Syndrome]
Hardy came with FF3b5, I installed FF2 only to discover that
none of the extensions that I was familiar with can be installed
like under Windows, there was always an error "230".
I tried some suggestions on forums such as disabling ipv6 support, but it didn't work.

Any ideas?
Thank you!

---

### Post by aheckler on 2008-04-30
I think you have to erase your Firefox profile first, located in ~/.mozilla/firefox. Once FF3b5 has used your profile directory, it becomes unusable for FF2. So make sure FF3b5 is uninstalled, then back up your bookmarks, saved sessions, etc. and delete your profile folder. Then install FF2 again and you should be good.

---

### Post by pricetech on 2008-04-30
Worked for me.  Thanks

---

### Post by kakyoism on 2008-05-01
Thanks aheckler. It worked!

---

