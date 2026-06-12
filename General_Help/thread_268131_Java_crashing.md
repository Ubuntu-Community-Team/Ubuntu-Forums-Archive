---
title: "Java crashing"
date: 2006-09-29
forum: General Help
---

### Post by graeder on 2006-09-29
I'm not totally sure if this is update related, but I ran updates a couple days ago on my system, now Java crashes all the time, using standard programs such as eclipse.  Again, I'm not 100% positive on the correlation with the recent update, but that's the only thing I can think of.  Prior to the update, everything was stable.  Anyone else experiencing this?

---

### Post by baldy1324 on 2006-09-29
i dont have any solutions but heres what ive got.
1. if you are using the packages from edgy eft (the testing version) file a bug report there at launchpad.net
2. if you are using 3rd party repositories or made your own java package with makejpkg. apt-get remove it. and uncomment the restricted and multiverse sections in your sources.list, run sudo apt-get update, and there is a package under sun-j2re or something like that.
3. if you are using the multiverse or restricted (forget which) packages from stable (dapper) then file a bug report for the java package

---

