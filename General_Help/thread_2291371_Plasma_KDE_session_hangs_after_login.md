---
title: "Plasma KDE session hangs after login"
date: 2015-08-19
forum: General Help
---

### Post by alain.roger on 2015-08-19
Hi,

i use for a week KUbuntu 15.04 on my computer (i7-3770, 32GB Ram, ATI Radeon R7-260x).
Everything works well except that for unknown reason today it hangs after login.

I can not get access to my work (email, devs, etc...) anymore and this is very bad.

I tried the fail safe mode, clean HD, and tried to clean cache but nothing worked. so once logged in i pressed CTRL+ALT+F12
i logged again with my standard user data (login/password)
and did
rm -fr ~/.cache/plasma*
rm -fr ~/.cache/ksycoca*
rm -fr ~/.cache/*.kcache
kbuildsycoca5

i reboot and everything seems to work, except that i do not have anymore my bottom panel where were all my icons and widgets like clock etc..
any idea if this is normal ?

thx.

---

### Post by alain.roger on 2015-08-19
in fact, i had to add again a default panel, and to replace all my application icons (launchers) on this panel. Even after several reboots, nothing appeared and then i had nothing else to do than to replace those icons.

---

