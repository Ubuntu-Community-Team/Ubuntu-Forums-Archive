---
title: "Apt-Get help with its switches"
date: 2008-01-12
forum: General Help
---

### Post by bigb_thedestroyer on 2008-01-12
I would like to know if there is a command line switch to download and install the suggested packages as well as the packages that I requested. 
I want to download the build-essential package and the suggested packages in one shot.

---

### Post by taurus on 2008-01-12
Just run

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by p_quarles on 2008-01-12
You'll need to use aptitude:
```
sudo aptitude -r install build-essential
```

---

