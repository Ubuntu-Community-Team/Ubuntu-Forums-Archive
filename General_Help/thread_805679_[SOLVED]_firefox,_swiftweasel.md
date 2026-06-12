---
title: "[SOLVED] firefox, swiftweasel"
date: 2008-05-24
forum: General Help
---

### Post by DarinB on 2008-05-24
i ended up having to clean install hardy...
firefox 3.0 can't install foxmarks get error can't install any plug in 
i installed swiftweasel 2.0.0.14 also can't install add-ons
i was recommeded to delete moz preferences then installed firefox 2
but lost all my emails in thunderbird. Pissed off!!!! i installed firefox 2

Add-ons still won't install?????? any ideas??????????

---

### Post by DarinB on 2008-05-25
sudo apt-get purge firefox-3.0
rm -r ~/.mozilla/firefox
sudo apt-get install firefox-2

awesome this worked for firefox then i 
tweaked it for swiftweasel then reinstalled 
swiftweasel 2.0.0.14 and it works and 
didn't kill my thunderbird

sudo apt-get purge swiftweasel 2.0.0.14
rm -r ~/.mozilla/swiftweasel

Go to swiftweasel get 2.0.0.14 for your build.

---

