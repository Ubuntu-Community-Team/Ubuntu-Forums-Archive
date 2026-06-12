---
title: "plasma 5.4.1 and 39 updates"
date: 2015-10-07
forum: General Help
---

### Post by alain.roger on 2015-10-07
Hi,

under kubuntu 15.04 i upgraded to plasma 5.4.1.
Since them, even i type:
```
sudo apt-get update && sudo apt-get upgrade
```

ubuntu always requests to install 39 upgrades....

is there a particular bug in plasma 5.4.1 ?

thx

---

### Post by deadflowr on 2015-10-07
Are they being held back?
apt-get upgrade only updates packages that already exist on the system.
If updates include new packages that need to be installed you need to run
```
sudo apt-get dist-upgrade
```

Of course, it also could just be kde being kde and the first 39 updates break 39 other packages which in turn get updates that break another 39 packages.
And so on.

---

### Post by Joelb955 on 2015-10-07
Could you post what the packages are? Just a few of them would be enough.

---

### Post by alain.roger on 2015-10-12
i upgrade it to 15.10 now so i do not have anymore this issue. Sorry

---

