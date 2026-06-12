---
title: "nvidia driver nvidia304"
date: 2019-06-04
forum: General Help
---

### Post by Finston on 2019-06-04
Any tips on how to get nvidia driver nvidia304 to install on ubuntu 18.04, please?

No UEFI or secure boot on my dual boot Mesh XP windows desktop.

---

### Post by kc1di on 2019-06-04
You can get 304.137 from this [ppa  ]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa") 
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-304
sudo apt install nvidia-settings
```

---

