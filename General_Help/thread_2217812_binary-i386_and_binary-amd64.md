---
title: "binary-i386 and binary-amd64"
date: 2014-04-18
forum: General Help
---

### Post by Aymenkn on 2014-04-18
Hey,
how I can solve this problem :(

```
W: Erreur de GPG : http://download.virtualbox.org quantal InRelease : Les signatures suivantes n'ont pas pu être vérifiées car la clé publique n'est pas disponible : NO_PUBKEY 54422A4B98AB5139
W: Impossible de récupérer file:/var/cache/apt-build/repository/dists/apt-build/main/binary-amd64/Packages  Fichier non trouvé

W: Impossible de récupérer http://ppa.launchpad.net/gezakovacs/boost/ubuntu/dists/saucy/main/binary-amd64/Packages  404  Not Found

W: Impossible de récupérer http://ppa.launchpad.net/gezakovacs/boost/ubuntu/dists/saucy/main/binary-i386/Packages  404  Not Found
```

---

### Post by oldos2er on 2014-04-18
Remove those PPAs from your software sources. ```
sudo rm /etc/apt/sources.list.d/gezakovacs*

sudo apt-get update
``` should do it.

---

