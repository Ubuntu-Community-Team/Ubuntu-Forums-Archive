---
title: "Can't install Nvidia Drivers"
date: 2020-02-08
forum: General Help
---

### Post by axelwebb on 2020-02-08
Hi everyone,

First that all, thank you very much your attention. I have an old DELL XPS laptop in home with Intel Core i5 and Nvida GeForce GT540M.  I was very happy with linux mint 17 but was time to updated it. I decided to install Ubuntu 19.10 this time but unfortunately i can't install correctly the Nvidia drivers. 

I have a few days trying to solve this issue. I made some research and reinstalled the system twice. My laptop has 2 graphics cards, the Intel and Nvidia one. As soon as I install the Nvidia drivers (Tried Nvidia390 and 340) I have the purple screen and the system crashed at the logging screen. I have been tried the "nomodeset"  and other variations and any of those work in my case (before the logging and/or editing the grub).

The only way to logg and work more or less fine without significant issue is selecting Intel by a Command Line: 
```
sudo prime-select intel
```

It seems that if the system is working with the Intel card works fine, but at soon as I change to the Nvida card the system crashed and did not logging. I will appreciate your comments in order to solve this issue and could use my Nvidia Card. Like I said Nvidia recommends the driver390 I installed it and also with the driver340 had the same results.

---

### Post by eyetinatim on 2020-02-10
Hi I had the same problem for months and I uninstalled my comodo internet security and tried the install again and IT WORKED.

---

### Post by CelticWarrior on 2020-02-10
The driver you need is 390. Also disable Secure Boot in UEFI settings.

---

