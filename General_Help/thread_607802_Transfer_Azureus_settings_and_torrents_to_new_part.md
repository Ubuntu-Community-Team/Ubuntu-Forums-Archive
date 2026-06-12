---
title: "Transfer Azureus settings and torrents to new partition"
date: 2007-11-09
forum: General Help
---

### Post by adt41287 on 2007-11-09
Does anybody know how to transfer my old settings and torrents from my old partition onto my new partition as easy and as painless as possible?

---

### Post by geirha on 2007-11-09
All azureus settings are stored in .azureus/ in your home-folder. All torrents are also stored in there by default. So, mount up the partition with your old home and ```
mv ~/.azureus ~/.azureus.backup # Just in case
cp -a /media/oldhome/$USER/.azureus ~/
```

---

