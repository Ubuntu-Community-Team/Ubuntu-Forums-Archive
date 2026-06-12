---
title: "broken packages?"
date: 2007-10-20
forum: General Help
---

### Post by stalefist on 2007-10-20
hi everyone, i'm getting this error when i try to install wine-

The following packages have unmet dependencies:
wine: Depends: libaudio2 but it is not installable
E: Broken packages

i did the following-
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

im getting the same error (i think with different packages however) when i try to install other apps too, like VLC, gstream, virtualbox...

does anyone know how to fix this or whats causing the problem?

---

### Post by LanDan on 2007-10-20
can you post your sources.list?

---

### Post by stalefist on 2007-10-20
i figured it out. i checked my sources and nothing was checked, so i just checked some boxes, did apt-get update/upgrade, and it worked. :D

---

