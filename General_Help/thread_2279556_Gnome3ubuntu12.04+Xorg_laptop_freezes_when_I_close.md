---
title: "Gnome3/ubuntu12.04+/Xorg laptop freezes when I closed the lid"
date: 2015-05-24
forum: General Help
---

### Post by alejandro30 on 2015-05-24
Well i 've having this issue for several weeks and it's annoying; not a clue on syslogs. The problem was with zeitgeist, as if it is unnseccesary for me i have uninstalled and finally it works, I can close the lid now and my system won't freeze anymore!:

zeitgeist-daemon --quit
sudo apt-get --purge autoremove activity-log-manager-common  activity-log-manager-control-center zeitgeist zeitgeist-core  zeitgeist-datahub
sudo rm -fr {/root,/home/*}/.local/share/zeitgeist

---

