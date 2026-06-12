---
title: "Need help connecting SimpleScan to printer"
date: 2021-10-07
forum: General Help
---

### Post by bm72 on 2021-10-07
Hi,

I just purchased a new HP printer. It does print fine. But it has also scanning abilities. When running the simpleScan software, I get the following message "no scanning device connected". It seems SimpleScan can't spot/connect my printer/scanner, though it has been properly installed (thanks to help from you Ubuntu community).

Also of note, my system/kernel is really old (see details below) and I can't seem to update, despite running "clean" "autoremove" and "update" commands as recommended by some helpful members here.

Thanks for your help. 


```
utilisateur@utilisateur-TravelMate-P253:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.5 LTS
Release:    18.04
Codename:    bionic
utilisateur@utilisateur-TravelMate-P253:~$ 
```

---

### Post by ActionParsnip on 2021-10-07
Bionic is still supported until 2023 so will receive updates and suchlike just as the latest Ubuntu versions.

---

### Post by ActionParsnip on 2021-10-07
How does the printer/scanner device connect to the system? Is it USB? What model HP device is it?

---

### Post by cmcanulty on 2021-10-07
For any HP printer it is good to install hplip to make all features work better

[https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index]("https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index")

---

